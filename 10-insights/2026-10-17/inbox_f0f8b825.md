---
id: inbox_f0f8b825
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0102-lobsters-vibecoding-ship-your-interpreter-26f8]]"
title: "Ship Your Interpreter"
url: https://www.basis.ai/blog/ship-your-interpreters/
source: lobsters-vibecoding
published_at: 2026-10-17T09:16:33-05:00
fetched_at: 2026-10-25T01:28:03.596880+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用機器證明的方式檢查 AI 寫的語言語意，而不是只靠測試。 **Why** 沒有形式語意的語言無法做數學證明，而 LLM 寫的語意可能有錯，測試又不一定抓得到。 **How** 把語言的直譯器編譯成語意已形式化的 RISC-V，讓 LLM 在 Lean 中證明其規則與編譯後 binary 的行為對所有程式都一致。 **What** 作者在 WHILE 小語言上實驗（直譯器為 1,855 行 C）；測試套件漏掉一個 63 位元組截斷的錯誤；後續計畫處理 Lua、OCaml，最終是 CPython。"
key_points:
  - "用 Lean 證明 LLM 撰寫的 WHILE 語意與編譯成 RISC-V 的直譯器 binary 行為一致（binary 含 25,336 條指令）"
  - "測試漏掉的錯誤：函式名超過約 59 字元時，字串串接結果與 binary 不同，原因是 snprintf 只寫入 63 字元"
  - "定理可雙向檢查：語意過寬或過嚴都會讓證明卡住，作者表示該義務通常指向錯誤的規則"
tags: [formal-verification, lean, formal-semantics, llm-proofs, interpreters]
topics: [engineering.evals, security]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Ship Your Interpreter

用機器證明的方式檢查 AI 寫的語言語意，而不是只靠測試。 **Why** 沒有形式語意的語言無法做數學證明，而 LLM 寫的語意可能有錯，測試又不一定抓得到。 **How** 把語言的直譯器編譯成語意已形式化的 RISC-V，讓 LLM 在 Lean 中證明其規則與編譯後 binary 的行為對所有程式都一致。 **What** 作者在 WHILE 小語言上實驗（直譯器為 1,855 行 C）；測試套件漏掉一個 63 位元組截斷的錯誤；後續計畫處理 Lua、OCaml，最終是 CPython。

### 重點
- 用 Lean 證明 LLM 撰寫的 WHILE 語意與編譯成 RISC-V 的直譯器 binary 行為一致（binary 含 25,336 條指令）
- 測試漏掉的錯誤：函式名超過約 59 字元時，字串串接結果與 binary 不同，原因是 snprintf 只寫入 63 字元
- 定理可雙向檢查：語意過寬或過嚴都會讓證明卡住，作者表示該義務通常指向錯誤的規則

**原文：** [lobsters-vibecoding](https://www.basis.ai/blog/ship-your-interpreters/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ship Your Interpreter

Every verified program starts from a semantics

A semantics can pass every test and still be wrong

Ship your interpreter

Developing the semantics and proof together

Separation logic makes the binary proof tractable

The theorem applies to real programs

Once you trust the semantics, the tools are cheap

What’s next: Lua, OCaml and, one day, CPython

Published: October 16, 2026

LLMs are growing alarmingly capable at finding and exploiting bugs in
production software, with increasing reports of AI-assisted hacks
in the wild.
Fortunately, LLMs are advancing quickly in their ability to write verified software : programs that come with mathematical proofs,
checked by a computer, that rule out entire classes of bugs.
In April, our agents built a JavaScript-to-WebAssembly
compiler but could not prove that it preserved
program behaviour. Months later, our agents verified Linux’s nftables
compiler , which translates firewall rules
into instructions the kernel executes. In September, MIT researchers
Frans Kaashoek and Nickolai Zeldovich used AI agents to verify the xv6
operating-system kernel down to its
machine code.

Our goal at Basis is to develop verification methods that could plausibly scale to all software, so that the systems powering critical infrastructure are secure by design and keep pace with attackers’ growing capabilities.
As LLMs advance in capability, the bottleneck is shifting away from theorem proving and towards the problem of specification: how can we be sure that the statements we prove capture the behaviour we actually care about?

To prove anything about a program, we first need a mathematical description of what it does.
This starts with describing the programming language it is written in: what every statement, loop, and function call means when it runs.
These descriptions are called a formal semantics , and can be written with pen and paper, but are increasingly expressed in a proof assistant such as Lean.
A handful of languages have one (Standard ML, WebAssembly, and C via CompCert), as does the RISC-V instruction set that a growing number of processors execute.
Developing each of these semantics took years of expert effort.

Most programs, however, are written in languages that do not have a formal semantics, presenting a major bottleneck for deploying verified software at scale: without a semantics, there is nothing precise to prove against.
A natural solution is to use LLMs to write semantics, but LLMs make mistakes, and a broken semantics undermines every proof built on it.
Testing helps, but as we show below, a semantics can pass every test and still be wrong. What is needed is a means to verify the semantics itself.

Languages without a formal semantics still have interpreters or compilers, which in practice define what their programs mean.
Here we consider a radical idea: make the LLM prove that its semantics agrees with the real interpreter on every program, treating the interpreter as ground truth. To do this, we compile the interpreter to RISC-V, whose meaning is already formally defined. That gives an exact, if unreadable, description of what the interpreter does with any program. The LLM then writes readable rules for the language and proves in Lean that, for every possible program, those rules predict exactly what the compiled interpreter prints. If a rule is wrong, the proof gets stuck.

We report on an experiment where we had LLMs develop a semantics and
its proof together for a small language. We used Lean to prove that the interpreter, the
program that runs code written in that language, follows those rules
even after being compiled into low-level machine instructions. The
whole development, semantics and proof, is on GitHub .
The rest of this post walks through this
experiment, explaining first why semantics are the bottleneck for
larger verification efforts and why tests aren’t sufficient to build
trust in them. We then show how the proof process refined the semantics,
how we handled the memory reasoning, and what tools we built on the result.

Before you can prove a program does anything, you have to define how
each operation transforms its state, that is, define its semantics .
Most languages describe their semantics informally in prose, in a
reference manual, and leave the concrete details to the compiler or
interpreter implementation. A formal semantics writes the rules down in mathematics, precisely enough for a
proof checker like Lean 4 to use them. Notable examples include
CompCert’s semantics for C, CakeML’s for ML, and JSCert’s for JavaScript.
Each one took years of expert effort, and often covers only a restricted
subset of its language.

For this experiment we used an extended version of WHILE, the small
imperative language used in textbooks such as Nielson and Nielson’s Semantics with Applications .
Our version has integers, strings, first-class functions with closures, if , while and for loops, and runtime errors. Its interpreter is 1,855 lines of
C, and a WHILE program looks like this (it prints 55):

The semantics an LLM wrote for WHILE is a set of rules, one for each
kind of expression and statement. These rules describe how to evaluate
an expression in terms of its subexpressions. For integer addition,
the rule is:

A rule reads from the bottom up. The line at the bottom is its
conclusion. Starting from state st in environment env , the
expression l + r evaluates ( ⇓ ) to c and leaves state st'' .
The state holds variable values, closures and everything printed so
far; the environment says which variables are in scope. The premises
above the line explain how the result follows from the subexpressions.
First l evaluates to a , leaving state st' . Then r evaluates to b in that state, leaving st'' . The final premise, a + b = c ,
adds the two integer values using WHILE’s 64-bit wrapping arithmetic.

Take (1 + 1) + x , with state [x ↦ 5] and environment {x} : x holds 5 and is in scope. Applying the rule gives:

That is, to evaluate (1 + 1) + x , we first evaluate (1 + 1) to get
2, then look up x to get 5, and add the two values to get 7. Neither
subexpression changes the state, so [x ↦ 5] remains unchanged.

To justify the first premise, we apply the addition rule again:

These rule applications form a tree that derives the value of the
whole expression from the values of its parts.

The LLM wrote about 400 lines of rules like these, in Lean ( the full
semantics ).
Each rule looks reasonable on its own, but an end user has no rigorous
way to tell whether they faithfully describe how WHILE programs behave
when they are actually run.

The usual way to check a semantics is to run it. Take a test suite,
run each program under the semantics and under the real interpreter,
and compare what they print. Unfortunately, in practice, this process
is insufficient to build trust in the generated semantics.

For example, an early version of our semantics passed the test suite
generated for the WHILE interpreter, but disagreed with the binary
when a function’s name reached 59 characters:

The semantics said that concatenating a function with a string would
include its full name between . The binary dropped the
closing > , and for longer names it dropped part of the name too.
No test in the suite tried functions with names this long.

The reason is in the C
interpreter that turns a value into a string when you concatenate it with + :

stringify returns a string value as it is. Any other value is first
printed into a 64-byte buffer on the stack and then copied into a
freshly allocated string. A named closure is printed with snprintf as , an anonymous one as , and the built-ins fall through
to the default case, .

snprintf writes at most 63 characters into the 64-byte buffer. The
initial semantics used the same rendering rule for concatenation and
printing, and missed this limit. To prove agreement with the binary,
the LLM had to give concatenation its own renderer. The corrected
semantics cuts a closure’s rendering to its first 63 bytes:

This is the kind of detail an
implementation accumulates internally but nobody writes down
explicitly, which is precisely why a semantics transcribed by hand, or
written by an LLM, can miss it. Nor is it a detail no program would
notice: code in dynamic languages routinely relies on the string form
of a function, for logging, for dispatch keyed on a name, or for
comparing serialised values. Even simple violations like
this undermine any verification effort built
on top of the semantics, and can leave holes that hide security
vulnerabilities. To build secure and scalable semantics, we need to go
beyond tests, since a test suite only checks the programs someone (or
an agent) thought to write.

Shipping your interpreter means checking the semantics against the
implementation people actually run. Compile the interpreter the
language already has, and make the LLM prove that the binary refines the semantics, that is, that the two agree on what every
program prints.

The theorem we proved is this one:

The theorem says for any WHILE program p , and any machine
configuration c , if the machine configuration satisfies a property Loaded , then the semantics match what the compiled binary will
do. Loaded interpRunLayout p (fillZero c) here says that c is a
machine about to run p through the interpreter binary. The first
conclusion, (∀ out, BigStep p out ↔ Halts c out 0) , says that the
semantics derives output out if and only if the machine halts with
exit code 0 having printed out , i.e. for successfully terminating
programs the predicted outputs are equivalent. The second says that any program p on which the machine runs forever ( Diverges c ), is a program the
semantics derives no terminating output for.

We can visualise this theorem as a commuting square , showing how the
semantics and the binary agree on a program’s output. In the diagram
below, the top arrow relates a program p to the output out predicted by the semantics. The bottom arrow relates a machine
state c to the output printed when the binary halts successfully.
The dashed line on the left is the Loaded condition connecting the
program to that machine state. Under this condition, the theorem says
the two outputs agree, shown by the double line on the right. The
orange arrow shows how a failed attempt to prove that agreement sends
the LLM back to revise a rule of the semantics.

The theorem catches a wrong semantics in both directions. If the
semantics is too permissive, it derives an output the binary never
prints, and the left-to-right half fails. If it is too strict, it has
no rule for something the binary does, and the right-to-left half
fails. Either way the LLM gets a proof obligation it cannot discharge.
In our experience, that obligation usually points at the rule that is
wrong.

RISC-V is an open processor design. We use its formal model, written
in Sail and translated into Lean,
to define how each machine instruction executes. The binary is the
actual ELF executable: 1,855
lines of interpreter C compiled by gcc, linked against dlmalloc and
newlib, 25,336 instructions in all. For comparison, the xv6 kernel
verified with MachCSL is 8,697 RISC-V instructions, built from 6,593
lines of C and assembly, although its proof also covers concurrency,
which ours does not need. The C compiler’s output, the C library and
the memory allocator are all inside our theorem. A person
who wants to trust the result reads the statement above, the hypothesis Loaded , and the two short definitions of Halts and Diverges . They
do not need to trust BigStep , because the proof checks it against the
binary.

Developing the proof forced the LLMs to account for four details in
the semantics:

Each correction started either as an obligation that would not close
or as a run of the binary that disagreed with the semantics.

The 63-byte cut is a representative example. The proof of the
concatenation case needed the semantics’ rendering to equal 

[... truncated for safety ...]

</details>