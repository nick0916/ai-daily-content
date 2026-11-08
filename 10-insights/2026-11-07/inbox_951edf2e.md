---
id: inbox_951edf2e
date: 2026-11-07
source_ref: "[[00-inbox/2026-11-07/0149-lobsters-ai-firecracker-vm-escape-pwnescape-part-2-4c8c]]"
title: "Firecracker VM Escape: PwnEscape Part 2"
url: https://pwn.ai/blog/firecracker-escape
source: lobsters-ai
published_at: 2026-11-07T02:44:02-06:00
fetched_at: 2026-11-08T01:56:52.040660+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "微型虛擬機的隔離被突破，攻擊者可在宿主機取得 root 執行權。 **Why** Firecracker 微型虛擬機常用來隔離不受信任的程式碼，這篇展示隔離被打破的完整路徑。 **How** 沿用前一篇的宿主記憶體存取能力，從 guest 找到 Firecracker 行程與 vCPU 的 pt_regs 暫存器框架，改寫 KVM_RUN 返回時的指令指標與堆疊，讓 Firecracker 執行 write(2) 輸出標記字串，之後還原堆疊。 **What** 測試對象為 Firecracker v1.16.1（x86-64、宿主 kernel 7.0.0-1011-aws），文中標示的 CVE 為 CVE-2026-99999；該設定未使用 jailer，作者表示生產環境的 jailer、namespace 與 seccomp 需另行評估。"
key_points:
  - "利用 guest 頁面的 GPA 與 nonce，透過 EPT 根節點搜尋找出宿主機實體位址，再反查 Firecracker 的 page table 與 ELF 載入偏移（load bias）。"
  - "KVM_RUN 系統呼叫期間，宿主核心保存的 pt_regs 可被修改；改寫後 vCPU 返回時執行 write(2) 輸出 N8V23M2 標記，再還原三個堆疊字。"
  - "測試環境以 root 經 systemd-run 啟動且無 jailer，因此受控呼叫以 root 權限執行；作者指出 jailer 會降權並限制 namespace 與 seccomp。"
tags: [firecracker, microvm, sandbox-escape, kvm, privilege-escalation]
topics: [security, engineering.architecture]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Firecracker VM Escape: PwnEscape Part 2

微型虛擬機的隔離被突破，攻擊者可在宿主機取得 root 執行權。

**Why** Firecracker 微型虛擬機常用來隔離不受信任的程式碼，這篇展示隔離被打破的完整路徑。

**How** 沿用前一篇的宿主記憶體存取能力，從 guest 找到 Firecracker 行程與 vCPU 的 pt_regs 暫存器框架，改寫 KVM_RUN 返回時的指令指標與堆疊，讓 Firecracker 執行 write(2) 輸出標記字串，之後還原堆疊。

**What** 測試對象為 Firecracker v1.16.1（x86-64、宿主 kernel 7.0.0-1011-aws），文中標示的 CVE 為 CVE-2026-99999；該設定未使用 jailer，作者表示生產環境的 jailer、namespace 與 seccomp 需另行評估。

### 重點
- 利用 guest 頁面的 GPA 與 nonce，透過 EPT 根節點搜尋找出宿主機實體位址，再反查 Firecracker 的 page table 與 ELF 載入偏移（load bias）。
- KVM_RUN 系統呼叫期間，宿主核心保存的 pt_regs 可被修改；改寫後 vCPU 返回時執行 write(2) 輸出 N8V23M2 標記，再還原三個堆疊字。
- 測試環境以 root 經 systemd-run 啟動且無 jailer，因此受控呼叫以 root 權限執行；作者指出 jailer 會降權並限制 namespace 與 seccomp。

**原文：** [lobsters-ai](https://pwn.ai/blog/firecracker-escape)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

00 / Choosing where to take control

01 / Finding our guest page on the host

02 / Finding the Firecracker process

03 / Locating the live vCPU frame

04 / Redirecting the return from KVM

05 / Checking execution and recovery

06 / Root execution on the host

Captured resolver values and artifacts

Proof of Concept

Technical references

Firecracker is supposed to keep untrusted code inside a microVM. We escaped it and achieved code execution as root on the host.

We found how it saved registers, changed where it would resume, and made it execute a call of our choosing when it returned from KVM. The guest then restored the temporary stack changes. Firecracker kept running, and the VM remained accessible over SSH.

PwnEscape Part 1 introduced the host memory primitive behind this work. Here we follow the next part of the chain: using that access to find Firecracker in memory and take over a live thread from inside the guest. This is a continuation to show CVE-2026-99999 on a Firecracker setup.

A Firecracker microVM has a process on the host that manages it. Each virtual CPU, or vCPU, has a thread in that process. The thread enters KVM to run the guest and returns to Firecracker when an event needs handling in userspace. Firecracker documents this arrangement in its architecture overview .

The call that runs the virtual CPU looks like this:

While the thread is in that system call, the host kernel holds its saved userspace registers in a structure called pt_regs . These registers describe the Firecracker thread: its instruction pointer says where execution should resume, and its stack pointer says which userspace stack it should use.

That made the return from KVM_RUN an attractive target. If we could locate and modify the saved frame, we could choose the code Firecracker executed when the thread returned to userspace. A guest operation that caused such a return would provide the trigger.

We already had access to selected host physical memory through a guest mapping. To use it, we needed to identify the Firecracker process, find code we could call in that process, and locate the register frame belonging to its active vCPU thread. The starting point was a page of memory we controlled inside the guest.

Figure 1. The guest identifies its Firecracker process, finds the saved registers for a vCPU thread, and redirects the thread when it returns from KVM.

The guest and host use different physical address spaces. A page has a guest physical address, or GPA, inside the VM and a host physical address, or HPA, in the machine backing it. On the target, Extended Page Tables (EPT) provide the translation between them.

We placed a recognizable byte pattern, a nonce, in a guest page. The first resolver took that page's known GPA and its contents as inputs. Together, they gave us an address to translate and a way to check whether the translation reached our page.

The resolver searched the host physical ranges covered by the memory primitive for candidate EPT roots. An EPT root is the starting point of the translation tables. For each candidate, the resolver followed the entries selected by the guest address until it reached a physical page, then checked that page for the nonce.

The snippets below are explanatory pseudocode with descriptive helper names. They show the data passed between stages and the checks used to connect them.

The nonce check connected a proposed translation to memory we controlled. The broader search produced two candidates; validation of the nested page tables reduced them to one EPT root. Walking that root gave us the host physical address of our guest page.

We called this result guest_page_hpa and passed it to the next resolver. We now had a recognizable object in host memory. The next task was finding the host process that mapped it.

Firecracker maps memory used by the guest into its own address space. That mapping gave us a way to work backward from the guest page to the process.

Host processes use page tables to translate their virtual addresses into physical memory. The top level is called the page global directory, or PGD. Recovering the appropriate PGD would let us translate addresses inside Firecracker and read its code and stack through the memory primitive.

Our reverse mapper searched the native host page tables for a mapping of guest_page_hpa . A normal page table walk starts with a virtual address and produces a physical address. Here, we looked for a mapping to a physical page we already knew, then recovered the virtual address and page table root associated with it.

The check runs in both directions:

This connected the host process's virtual mapping to the physical page found through EPT. The reverse mapper returned one validated address space. We retained its root as host_pgd and used it to inspect the process.

The next resolver looked for the Firecracker executable in those mappings. It identified an ELF image and checked a known byte sequence in Firecracker's write(2) wrapper. That connected the recovered address space to the binary we were targeting.

ASLR changes where an executable is loaded. The difference between an address in the ELF image and its corresponding runtime address is the load bias. Once the mapper had identified the image, it could recover that bias and use it to locate the code required by the exploit:

The mapper returned the load bias as firecracker_base . With that value and host_pgd , we could locate code in the running process, translate its virtual address to host physical memory, and compare the bytes there with the expected binary.

We checked three locations: the write(2) wrapper that would produce our proof, the continuation after the KVM ioctl, and a short xor eax,eax; ret sequence needed to return cleanly. Their purposes become relevant when we construct the return path below.

At this point, the guest could inspect the Firecracker image and its private mappings. We still needed the saved registers of the thread currently running our VM.

Figure 2. The nonce identifies the guest page in host memory. Its mapping leads to a host page table root, which lets the next resolver locate and validate the Firecracker image.

The frame finder took host_pgd and firecracker_base from the preceding stages. It used them to recognize the host thread's saved state.

The most useful clue was the return address. A vCPU thread in KVM_RUN should have a saved instruction pointer at the corresponding ioctl continuation in Firecracker. We could calculate that address from the validated binary and its load bias.

We then searched host memory for a pt_regs frame consistent with that call. An address match alone would also pick up stale stack contents, so the candidate had to satisfy several related checks:

The stack check tied the frame to the same address space we had recovered from the guest page. The instruction and caller addresses tied it to the Firecracker image. The syscall fields tied it to the operation running the vCPU.

The search left one candidate. Its location was stored as frame_hpa , the host physical address of the saved register frame. We passed it, the PGD, and the load bias to the final helper.

Before changing memory, the helper repeated the code signature, frame, and stack checks. This ensured that the active stage used the same process state the resolvers had identified. The subsequent execution and recovery checks would establish that the selected frame was live.

Figure 3. The candidate register frame must agree with the KVM ioctl, the recovered process page tables, and the validated Firecracker code.

We chose a simple payload: make the Firecracker process write a recognizable string to its own stderr. This would give the host runner an observable result from the process we had taken over.

The string was N8V23M2\n , seven characters followed by a newline. It occupies eight bytes and fits in one stack word. The call we wanted Firecracker to execute was:

Here 2 is Firecracker's stderr file descriptor. The buffer pointer must refer to the string in Firecracker's address space, so we stored the string on its private userspace stack.

We saved three stack words before modifying them. One held the string; the other two held the return addresses for the temporary call sequence. We then changed the saved register frame to supply the wrapper address, its arguments, and a stack pointer for that sequence:

Returning from write also needed care. A successful write of eight bytes returns 8 , while a successful KVM_RUN call returns zero . We placed the address of xor eax,eax; ret first in the return sequence. It clears the return value before the second address brings execution back to Firecracker's original ioctl continuation.

The resulting control flow was:

With the stack and saved registers prepared, the guest wrote one byte to its serial port. That operation caused the vCPU thread to return from KVM_RUN . The kernel restored the modified registers, and Firecracker entered the write wrapper with our arguments.

The wrapper emitted the marker, the return sequence cleared eax , and the thread rejoined its original execution path. After control returned to the guest, the helper restored all three stack words.

Figure 4. The saved register frame enters the write wrapper. Two return addresses lead through the return-value adjustment and back into the original Firecracker path.

The host runner captured Firecracker's stderr separately from the guest. The complete output was:

The capture contained exactly eight bytes, including the final newline. Firecracker was still running, guest SSH was responsive, and the helper had restored the three temporary stack words.

We checked recovery with a fresh pass that made no memory changes. It was given the same frame address and repeated the register, code, and stack checks after the trigger. The checks passed, and it found no stale marker in the temporary stack location.

These observations answered three different questions. The guest log recorded the trigger and restoration. The host capture showed that Firecracker executed the selected operation. The final validation checked the state after execution.

Figure 5. The guest log, Firecracker stderr capture, and final validation record the trigger, host execution, and restored state.

By the time the marker appeared, the guest had selected the host thread's instruction pointer, function arguments, stack data, and return path. Firecracker executed the call using its own privileges.

The target was Firecracker v1.16.1 on x86-64, with host kernel 7.0.0-1011-aws and guest kernel 6.18.44+ . We launched Firecracker directly as root under systemd-run and pinned it with taskset . Consequently, the controlled call executed as root on the host.

The existing write wrapper gave us a compact proof of that control. Extending it to other calls would require choosing code and arguments compatible with the process's mappings and syscall policy.

The configuration used here had no jailer. Firecracker's production containment includes dropping privileges and restricting the process through namespaces and seccomp. A deployment using those controls requires a separate assessment of the privileges and resources available after compromising its VMM.

The address discovery is what lets the exploit follow the running instance. The EPT resolver connects a guest page to host memory; the reverse mapper recovers the host address space; the image mapper locates Firecracker under ASLR; and the frame finder identifies the vCPU's saved state. Adapting the final stage to another build requires validating that binary's code signatures and return path.

The guest had used access to host memory to take over the thread running the VM itself. A serial write supplied the trigger, and the next userspace operation belonged to us.

The following values come from the preserved execution record. The methods above use symbolic names so that the role of each value is c

[... truncated for safety ...]

</details>