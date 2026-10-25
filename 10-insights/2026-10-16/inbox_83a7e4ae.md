---
id: inbox_83a7e4ae
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0102-lobsters-vibecoding-what-agents-mean-for-rust-and-vice-versa-73a2]]"
title: "What agents mean for Rust (and vice versa)"
url: https://smallcultfollowing.com/babysteps/blog/2026/10/14/agentic-dev-and-rust/
source: lobsters-vibecoding
published_at: 2026-10-16T06:26:57-05:00
fetched_at: 2026-10-25T01:28:46.809328+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Rust 因型別系統與效能旋鈕適合 AI agent，但作者認為仍需證明工具才能確保正確性。 **Why** 作者認為 agent 時代測試不足以證明程式正確，型別系統能排除錯誤但不保證正確，因此需要證明系統。 **How** 作者主張利用 Rust 的型別與借用檢查縮小 agent 出錯空間，並以 Verus、Creusot、Aeneas、Kani 等工具證明 panic-free 或功能正確性。 **What** 作者提出 Rust 的北極星目標「不再需要 unsafe code」，即能證明所有 unsafe 程式碼不會造成 undefined behavior；介面與實作分離、規格設計仍被列為未解問題。"
key_points:
  - "效能：agent 能協助調整 Rust 的效能旋鈕（堆疊/堆積配置、struct layout、async 邊界），並搭配 profiler 形成回饋迴路，文中提到 dial9 用於診斷 async 效能問題"
  - "可靠性：「能編譯就大致正確」是 Rust 的優勢；型別系統只保證避免特定錯誤，要證明正確性需要 Verus、Creusot、Aeneas、Kani 等證明工具"
  - "北極星：「no more unsafe code」，意指能證明 unsafe 程式碼正確，從而在不冒風險下積極最佳化"
tags: [rust, ai-agents, formal-verification, type-systems, unsafe-code]
topics: [agents.coding_agents, engineering.evals, security]
importance: 4
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## What agents mean for Rust (and vice versa)

Rust 因型別系統與效能旋鈕適合 AI agent，但作者認為仍需證明工具才能確保正確性。 **Why** 作者認為 agent 時代測試不足以證明程式正確，型別系統能排除錯誤但不保證正確，因此需要證明系統。 **How** 作者主張利用 Rust 的型別與借用檢查縮小 agent 出錯空間，並以 Verus、Creusot、Aeneas、Kani 等工具證明 panic-free 或功能正確性。 **What** 作者提出 Rust 的北極星目標「不再需要 unsafe code」，即能證明所有 unsafe 程式碼不會造成 undefined behavior；介面與實作分離、規格設計仍被列為未解問題。

### 重點
- 效能：agent 能協助調整 Rust 的效能旋鈕（堆疊/堆積配置、struct layout、async 邊界），並搭配 profiler 形成回饋迴路，文中提到 dial9 用於診斷 async 效能問題
- 可靠性：「能編譯就大致正確」是 Rust 的優勢；型別系統只保證避免特定錯誤，要證明正確性需要 Verus、Creusot、Aeneas、Kani 等證明工具
- 北極星：「no more unsafe code」，意指能證明 unsafe 程式碼正確，從而在不冒風險下積極最佳化

**原文：** [lobsters-vibecoding](https://smallcultfollowing.com/babysteps/blog/2026/10/14/agentic-dev-and-rust/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Rust is popular in the agentic era

Foundational Software construction with agents

Rust and optimization: fast by default, knobs when you need ’em

Reliability is king, as always

Testing is not enough, type systems help

Type systems are not enough either

Strong guardrails give better performance

If we are going to prove things, do we need type systems?

Where I think Rust should go on reliability

A north star: No more unsafe code

Design is an open problem

Conclusion

As someone who has made a career of programming language design, I definitely have moments of existential dread about the rise of LLMs. I started coding in 5th grade on an x86 1 that ran at 5MHz, had something like a 5MB hard-disk and 512K of RAM 2 . Computers were really, really different back then. But honestly, programming wasn’t. For all the advances in IDEs and programming languages and so forth, the basic act of entering code into a file has remained surprisingly constant 3 – right up until a few years ago, when everything kinda turned on its head. That’s been exciting and empowering at times 4 but also scary and disorienting. Will my skills in programming matter? What about my skills in programming language design (such as they are)? This blog post is my attempt to answer those questions.

So as not to keep you in suspense, let me just give you the conclusion. In short, yes, I believe there will still be a role for humans in programming . And yes, I think that programming language design is still relevant . And, naturally, I also happen to think Rust is a really good fit for agentic development – but that’s not to say we can’t make it a better fit . And that’s what this post is ultimately about: what makes Rust and agentic development work well, and where we could double down on those strengths.

This is a kind of “blog post companion version” of a talk I gave this week at REBASE, part of SPLASH . You might also enjoy the slides from the talk I gave at IWACO, IWACO and Rust: hidden links revealed , which was a bit more of a retrospective (no soundtrack for those, though). In any case, this turned out to be a great conference! Jack Huey presented on the Rust Vision Doc and, quite to my surprise, Steve Klabnik and Dorian Scheidt presented “LLMs as Collaborators in Language Specification and Design” , talking about their process in building out Rue . It was fun to see Steve again. On top of that, there was a ton of great research presented at IWACO in particular. I was particularly taken by the work on Reachability Types and Information Borrowing . I also really liked learning about Hylo Lang , particularly their approach to projections. Clever and cool.

Rust is popular right now. Very popular:

Stratospheric among the breakout languages is TypeScript, cropped from the chart and sitting currently at +1200% growth from the prior year. [..]

The second most rapid recent growth is in Rust. Meta engineers have written twice as much first-party Rust code so far this year than in the previous 9 years combined.

— David Tolnay (emphasis mine)

Some of that is because agents make it very easy to try out new things. And some of that is because Rust has a reputation for being performant and, if it’s just as easy to pick any language, why not pick one that will yield faster execution times?

But I think Rust is popular for another reason: because Rust happens to be a really good fit for agentic coding 6 . Of course, I would, wouldn’t I? The point of this post is (1) to argue for why that is and then (2) to discuss what we might change about Rust to make it work even better.

It seems to me that an effective “software factory” will have three pillars:

None of these pillars are solved, but some have made more progress than others.

Rust is designed to give “good performance by default”, making the idiomatic thing typically also be the fastest thing. But another key part of Rust is that you have the knobs to eke out better performance when you need it. You control when something is stack- or heap-allocated and where pointer indirection occurs. If you want to, you can force the layout of your structs to be done in a particular way, or decide where to introduce boxing into your async stack frames. In the limit, you can put in inline assembly.

In the past, learning how to “tune the performance knobs” could be a bit of a black art: but agents are making that much easier. 7 It turns out that agents are really good at fine-tuning the performance of existing code. For example, people who work on super high-performance cryptographic algorithms used to do so by hand-tuning assembly code. But those people tell me that they are now turning to agents for that same job. More prosaicly, a lot of people building network services are finding that, using a profiler like dial9 , agents can quite effectively diagnose async performance pitfalls, like long polls or blocking.

Therefore, I think the task for Rust is clear. We keep on with our goal of “low-level enough for a kernel, high level enough for a GUI” . If anything, I think the shift around agents means we can tolerate a bit more “noise” in the form of explicit calls to clone() or share() – but not too much, since we still want the “happy path” of the code to be clear and evident 8 , even as we surface details that are important in specific scenarios (like tracking precisely how many clones you have of a channel endpoint). Combined with a profiler, you get an effective feedback loop to get your code running fast:

As usual though, while a reputation for good performance is what brings people to Rust, what makes them want to stay is a sense that using Rust “just seems to work better”. The basic theory is that Rust’s type system and guardrails help keep agents on track :

rust is a perfect language for agents, given that if it compiles it's ~correct

I think there’s truth in that: languages like Rust, Ocaml, or Haskell all share this “if it compiles, it works” feeling, and I think that agents will benefit from that.

Testing can show the presence of bugs, but not their absence.

— Edsger W. Dijkstra, 1970

Writing tests has never been enough to show that your program is correct – but, with agents, it’s not even close. It happens so often that my first few tests seem great and then the next one goes completely bonkers. Usually bonkers in a way where I cannot even imagine how that bug could have come about. Then I dig in and I realize the agent completely missed the boat on the logic I was trying to express. 9

This is where a type systems really shines – particularly an advanced one like Rust. Type systems give you some guardrails that keep the agent on track. In Rust, those guardrails extend beyond simple stuff like “do all fields have the correct names” and to stuff like never having to close a socket .

Type systems can show the absence of bugs, but not the presence of correctness.

— Me, failing to coin a phrase of equal eloquence 10 , 2026

So yeah, type systems are helpful! But they have inherent limits. A type system is a simple set of rules that, if you follow them, make sure that you avoid (certain kinds of) mistakes. But they don’t tell you that you do the right thing – only that you don’t do (certain kinds of) wrong things . If you want to go further, you need a proof system – something that will let you show that richer properties are actively true, not just that you’re avoiding bugs.

As it happens, there are a lot of interesting proof tools for Rust, like Verus , Creusot , Aeneas , and Kani . As a starting point, you can prove that your code is panic-free, which will eliminate a lot of bugs, though it is still fundamentally a “type-checker-like” property (i.e., you avoid doing things wrong). But you can also go further and add assertions that show your code is computing the results you expect.

Deplying proofs is not just good for getting code right – it’s good for getting code fast . This is somewhat counterintuitive, but it’s true. Earlier I mentioned how optimized cryptographic algorithms were now being written by agents . Part of what makes that possible is that cryptographic algorithms have a very clear mathematical definition. This means that you can basically tell the agent “do whatever you want, as long as you can prove that the code still computes the correct result”. These proofs can be done with theorem provers like Lean or Rocq . The blog post “Why Lean is faster than Rust” makes the point quite well.

For Rust, a good example of this would be around unsafe code. Right now, people are sometimes reluctant to deploy unsafe code even if it might make their code faster because it’s not worth the risk of getting it wrong. And I applaud that effort. But what if you could use a prover to show that your unsafe code is, in fact, safe (i.e., incapable of causing undefined behavior)? Then you’d be free to optimize to your heart’s content.

You might wonder: if we’re deploying a proof system on our code, do we still need type systems? I think the answer is definitely yes. Type systems are infinitely simpler to work with, which is why they are much more popular. Using a type system lets you rule out all kinds of annoying bugs so that you can focus your “proof energy” only on the important stuff.

As a simple example of this, consider the following Java code:

Without seeing more code, it is impossible to prove whether this assertion is true or not! This is because there could be any number of other threads running around mutating this . In contrast, the following Rust code must be true (at least, so long as the Eq operator is reflexive for Bar ):

We know this because the type system of Rust guarantees that &mut self implies a unique reference.

This is in fact exactly how Verus works. By trusting the Rust borrow checker to track uniqueness etc, it simplifies the job of the SMT solver, making proof checking must faster and more reliable than it would be otherwise.

So my take is that Rust should double down on if it compiles, it works . As expressive as Rust’s type system is, there are plenty of things that it cannot capture. This includes fairly common things, like this method only reads one particular field or internal references , but also fancy things like “no logging of personally identifiable information”. We should work to lift those limits, giving agents room to prove more complex properties.

We also need to improve the experience of integrating a proof tool by working towards an extensible compiler . As cool as the existing Rust-based proof tools are, using them is a janky experience involing annoying macros and pinned compiler versions. We can do better.

I’d like to propose a north star for Rust: no more unsafe code . By that, I don’t mean that we never use the unsafe keyword . Rather, I mean that we have the power to prove that all the unsafe code we write is correct and cannot cause undefined behavior. Don’t get me wrong: knowing exactly what code needs to be vetted is a huge step forward, as is normalizing the idea that libraries need to be responsible for protecting their users from undefined behavior via safe API boundaries 11 . But given agents’ ability to find vulnerabilities, I think we need to up-our-game if we want to stop the steady stream of CVEs. 12

But before you go about proving things or optimizing them, you need to have a clear idea of what you are building. As far as I can tell the state of the art here is basically variations on “markdown-driven-development”, developing docs and hoping that agents pay attention.

I don’t know how much of a role for Rust there is in this space. I think there are some steps we might wind up taking that could be helpful here – for example, having ways to separate out interface from implementation so that it’s easier to review the interface in isolation or to see when the agent made changes there. 13 Or perhaps just providing betters tools to review that.

I also think there’s space for dedicated “

[... truncated for safety ...]

</details>