---
id: inbox_800f9caa
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0102-lobsters-vibecoding-pwnescape-guest-to-host-kvm-escape-cve-2-27a6]]"
title: "PwnEscape: Guest-to-Host KVM Escape (CVE-2026-99999)"
url: https://pwn.ai/blog/pwnescape
source: lobsters-vibecoding
published_at: 2026-10-17T13:24:39-05:00
fetched_at: 2026-10-25T01:27:20.258466+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Linux 網路堆疊的延遲 checksum 漏洞可讓 guest 在 KVM 沙箱中逃逸至主機，編號 CVE-2026-99999。 **Why** 沙箱隔離不只靠 hypervisor，主機網路堆疊若在延遲寫入時信任未再驗證的 metadata，就會破壞安全假設。 **How** guest 可控的 checksum metadata 在核心驗證後、分片輸出前被完成寫入，使 IPv4 header 的 IHL 由 0x45 變為 0x4f，後續程式以錯誤的 header 長度解讀封包。 **What** 研究者在 Vercel 100 萬美元沙箱挑戰中發現此問題，Vercel 將其列為該計畫唯一的 Critical 發現；上游修補為 6785011f8b16。原文已截斷，本摘要僅依可見段落。"
key_points:
  - "漏洞位於 Linux 網路堆疊（CVE-2026-99999，Critical），上游修補 commit 為 6785011f8b16「ipv4: validate checksum_start before completing checksum」"
  - "機制：CHECKSUM_PARTIAL 的延遲 checksum 寫入，會依 guest 可控的 metadata 改寫已驗證的 IPv4 header，例如 IHL 由 0x45 改為 0x4f"
  - "作者提出「deferred-metadata trust inversion」為更廣的失效模式；原文截斷，後半技術細節未提供"
tags: [linux-kernel, kvm-escape, sandbox-security, checksum-offload, cve]
topics: [security]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## PwnEscape: Guest-to-Host KVM Escape (CVE-2026-99999)

Linux 網路堆疊的延遲 checksum 漏洞可讓 guest 在 KVM 沙箱中逃逸至主機，編號 CVE-2026-99999。

**Why** 沙箱隔離不只靠 hypervisor，主機網路堆疊若在延遲寫入時信任未再驗證的 metadata，就會破壞安全假設。

**How** guest 可控的 checksum metadata 在核心驗證後、分片輸出前被完成寫入，使 IPv4 header 的 IHL 由 0x45 變為 0x4f，後續程式以錯誤的 header 長度解讀封包。

**What** 研究者在 Vercel 100 萬美元沙箱挑戰中發現此問題，Vercel 將其列為該計畫唯一的 Critical 發現；上游修補為 6785011f8b16。原文已截斷，本摘要僅依可見段落。

### 重點
- 漏洞位於 Linux 網路堆疊（CVE-2026-99999，Critical），上游修補 commit 為 6785011f8b16「ipv4: validate checksum_start before completing checksum」
- 機制：CHECKSUM_PARTIAL 的延遲 checksum 寫入，會依 guest 可控的 metadata 改寫已驗證的 IPv4 header，例如 IHL 由 0x45 改為 0x4f
- 作者提出「deferred-metadata trust inversion」為更廣的失效模式；原文截斷，後半技術細節未提供

**原文：** [lobsters-vibecoding](https://pwn.ai/blog/pwnescape)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Part 00: Intro

Research

Part 01: A deferred checksum and a mutable IPv4 header

01A / We went looking beyond the hypervisor

02 / CHECKSUM_PARTIAL is a promise to write later

03 / The header was checked. Then the header changed.

04 / Where the 32 bytes actually came from

05 / Why this was an escape primitive, not just a leak

06 / The broader failure mode: deferred-metadata trust inversion

07 / What Linux actually changed

08 / Research notes: three days to the primitive, weeks to the fix

09 / Why this matters to people building sandboxes

The input-side comparison was not enough

A simplified control-flow trace

Why the proof needed controls

Special Thanks

Technical references

How a $1 million sandbox challenge led us to a vulnerability in Linux networking, repeatable host-memory disclosure, and ultimately a full guest-to-host escape.

On August 18, 2026, Vercel announced a $1 million challenge inviting researchers to break the isolation boundary of its Sandbox product (total prize pool). The announcement came just weeks after OpenAI had disclosed a remarkable security incident : AI agents running inside restricted evaluation environments had found ways around their network isolation, compromised internal infrastructure, and eventually breached systems at Hugging Face. The agents weren't supposed to have internet access in the first place.

But there was an important distinction. Escaping a sandbox's network restrictions is one thing. Escaping the virtual machine itself and reaching the host is another. Vercel's challenge explicitly invited researchers to attempt both. We were interested in the latter. (Although we ended up finding vulnerabilities that also allow the former - more on those findings in a later post)

The question was simple: how much could an untrusted guest influence the host kernel without ever exploiting KVM itself? We took the challenge, put our research infrastructure to work, and within three days discovered a primitive buried in Linux networking that allowed guest-controlled checksum metadata to rewrite an IPv4 header after the kernel had already validated it .

What initially looked like a 32-byte host-memory disclosure would eventually become a full guest-to-host escape in our own KVM and many many other Hypervisor environments. And the beautiful part about it was that the vulnerability wasn't even in the hypervisor, it was in the Linux networking stack.

Vercel later described it as the program's most important report , and its final tally recorded just one Critical finding. That Critical was what is now pwnescape. Together with a separate network-escape report, we had accomplished both network and host escape goals. Its important to emphasize Vercel's sandbox was already hardened beyond normal industry standards and had no misconfigurations we could spot. Although the vulnerability originated in the Linux kernel and wasn't a Vercel-specific flaw or misconfiguration, Vercel deserves tremendous credit for how they handled it. They moved quickly to protect their customers, launched their own independent research, identified and notified other affected hypervisor and sandbox providers, and worked closely with us to coordinate disclosure and fixes across the industry. Their efforts helped protect not just Vercel's customers, but the wider ecosystem.

This is the story of CVE-2026-99999, a Critical rated Linux kernel vulnerability leading to KVM escape.

We used Omega-Pwn, pwn.ai's experimental research harness combining our custom security architecture and automation with elements of OmegaClaw , developed by researchers at SingularityNET and BGI Labs for this ambitious project. Compared to traditional LLM harnesses, it enabled longer research horizons, persistent campaign state, parallel collaborative investigations, and the accumulation of hypotheses, failed experiments, and evidence across complex research sessions.

Humans led the research, framing the hard questions, engineering workflows, and directing investigations. GPT-5.6 Sol served as the primary reasoning engine for source-level analysis, exploring attack paths, and challenging assumptions. Omega-Pwn bridged human intuition and contextual insight with the analytical capabilities of advanced LLMs.

As far as we know, PwnEscape exposes an entirely new class of attacks in Linux networking: untrusted checksum metadata can rewrite security-sensitive packet fields after the kernel has already validated and acted on them, undermining assumptions across the networking stack far beyond the original VM escape.

The accepted Linux fix is upstream as 6785011f8b16 , ipv4: validate checksum_start before completing checksum .

This is the first installment of PwnEscape . We are going to spend most of it inside sk_buff , checksum metadata, and IPv4 fragmentation, because that is where the actual failure happened.

Figure 1. The vulnerable component is the host networking stack. “KVM escape” describes the guest/host security boundary crossed in our isolated proof, not the source file that contained the bug.

Our previous kvmCTF research was about KVM's shadow-MMU behavior: an intricate interaction among mappings, reverse maps, and memory lifetime. This campaign began with a broader hypothesis. The security of a sandbox depends on much more than its hypervisor. A guest interacts with an entire host operating system, including device emulation, virtual networking, packet filters, memory allocators, and the APIs that glue those pieces together.

For pwn, that suggested an efficient research strategy: map the reachable boundary, search for places where untrusted state gets promoted to trusted state, and challenge the assumptions at every later consumer , not just at the initial parser. We used GPT5-6-Sol-assisted source inspection with human set the scope and decide what actually constitutes evidence. The particularly interesting question at this time was:

Can an asynchronous or deferred operation modify packet bytes after the kernel has already made security-relevant decisions about those same bytes?

Linux checksum offload offered exactly that possibility.

Linux does not always compute transport checksums immediately. Instead, it can carry a packet in a state where the checksum still needs to be completed. The relevant sk_buff bookkeeping includes:

This is normal, documented functionality. On the transmit side, a network device or the software helper skb_checksum_help() can calculate the checksum and store the result at the designated field. In well-formed TCP/UDP traffic, that field belongs to the transport checksum. In the ordinary kernel path, the metadata is supposed to describe the packet that actually exists. See the kernel checksum-offload documentation .

The critical point is that these values are not just descriptive metadata . They authorize a subsequent write into packet memory. If less-trusted software can influence them, their validity must survive every operation between admission and completion.

An sk_buff also has multiple notions of where packet data begins:

The distinction between the frame-relative view and the network-header-relative view is important. A packet can arrive with Ethernet and additional link-layer headers still in its linear data. Later, those headers are removed or skipped for L3 processing. Merely checking that a checksum start falls far enough into the original frame is not the same as proving that it follows the IPv4 header after normalization.

Figure 2. The accepted packet's link-layer context is not the final IPv4 context. The issue is a mismatch of stored metadata and the current network-header boundary, not that the physical allocation magically moves. Our original reports cover the exact packet geometry; this figure focuses on the broken invariant.

The first public patch series makes the entry-path defect especially clear. In __virtio_net_hdr_to_skb() , the historical minimum-header check used skb_transport_offset(skb) , an offset relative to the current skb->data view. That protects against a checksum start that is trivially too early in that view. It does not by itself establish how far the start is from the network header when the packet contains additional link-layer structure.

The original reported hardening therefore proposed an additional network-relative comparison:

Those two inequalities are not interchangeable. The distinction is the essence of the L2/L3 coordinate mismatch. The patch review grew beyond this first formulation because nested headers, IP options, IPv6, and differing ingress callers require more careful validation than a single optimistic fixed offset. Our original input-side patch and Willem de Bruijn's later proposed broader input validation provide the source-level history.

For the eventual IPv4 consumer, the accepted guard expresses a particularly useful invariant. With N = skb->network_header , H = ip_hdrlen(skb) , C = skb->csum_start , and nonnegative checksum offset O , the eventual output location is W = C + O . Requiring C >= N + H before completion implies W >= N + H . The guard therefore prevents this completion from writing into the IPv4 header . It does not prove that W is the correct field within TCP or UDP; that is a separate protocol-validity question.

This is the first trust failure: checksum metadata from a less-trusted origin crossed into host packet processing without being constrained against the header that later code would actually use.

The most interesting part is the order of operations.

Host ingress sees and parses an IPv4 packet with an ordinary header. Fragment processing and routing can operate on that state. Later, output fragmentation reaches the pending checksum. In the historical code, ip_do_fragment() completed the checksum before obtaining the IPv4 header pointer and using the header length. The pre-fix ordering in net/ipv4/ip_output.c was effectively:

skb_checksum_help() is not inherently unsafe. It becomes unsafe here because malformed metadata allows its write to overlap bytes that were already parsed as an IPv4 header .

The header field that gives the leak its shape is IPv4 ihl , a 4-bit count of 32-bit words. The first byte of a normal IPv4 packet contains version and IHL. In our controlled research geometry, it could change from 0x45 (IPv4, five words = 20 bytes) to 0x4f (IPv4, fifteen words = 60 bytes), without changing the version nibble.

Figure 3. A two-byte header mutation can leave the packet looking like IPv4 while dramatically changing the header-length interpretation. 0x4500 and 0x4f00 are the before/after first words observed in the research case.

Static IHL readout

The IPv4 version nibble remains 4 ; only the four-bit header-length interpretation changes.

The earlier stages had not endorsed a 60-byte header. They had made decisions on a 20-byte header. But the later consumer read an updated field as though it were authoritative.

This is a time-of-check/time-of-use problem in the semantic sense , but not the usual race between threads. The execution can be fully deterministic. The “time” separating validation and use is the sequence of legitimate networking operations, with an attacker-influenced deferred write in between.

This is an example of vulnerability-oriented path diagram, not a claim that every network configuration takes precisely these exact hooks, although we have found numerous other methods to invoke these vulnerable paths.

This part is easy to explain poorly. Linux packet buffers need not contain all packet bytes as one contiguous linear object. An sk_buff has a linear head plus possible non-linear fragment data. After the relevant reassembly, the research case's logical linear data length was just:

The late checksum operation made the fragmenter believe that the IPv4 header was 60 bytes long. That means it treated the next 40 bytes after the original 20-byte header as IPv4 options. Eight of those bytes were genuinely inside the linear head, 

[... truncated for safety ...]

</details>