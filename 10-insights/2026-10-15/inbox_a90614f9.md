---
id: inbox_a90614f9
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0102-lobsters-vibecoding-rust-djinn-you-should-specify-your-code-24f6]]"
title: "rust-djinn: You Should Specify Your Code Unambiguously (and Prove That You Did)"
url: https://henniger.dev/post/djinn/
source: lobsters-vibecoding
published_at: 2026-10-15T10:36:45-05:00
fetched_at: 2026-10-25T01:28:46.811835+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "以 djinn! 巨集在 Rust 中寫規格，由 LLM 實作並經 Aeneas/Lean 證明後編譯。 **Why** 作者認為規格易寫錯或寫不完整，LLM 加驗證器可在不逐行審查程式碼下確保實作符合規格。 **How** cargo djinn implement 將規格轉為 Aeneas 的 proof obligation，啟動 LLM agent 撰寫程式並證明，再由 Lean 檢查；加入 unambiguity constraint 要求規格不容許實質不同的實作。 **What** 作者以 gzip 解壓為例，經 Codex 與 Claude Code 交替優化 100 輪，文中稱其略勝 zune_inflate 等測試過的實作，且未使用 unsafe 或 C 函式。"
key_points:
  - "流程：cargo djinn implement 一次完成翻譯成 Aeneas、啟動 LLM agent、驗證；cargo djinn optimize 以 benchmark 做 hillclimbing，效能不進步的版本會被丟棄"
  - "unambiguity constraint：要求證明不存在與規格實質不同的實作，以抵抗規格遺漏（例如忘了輸出必須是輸入的排列）"
  - "gzip 解壓：約 300 行規格（含壓縮），文中稱 rust-djinn 在純 safe Rust 中略勝 zune_inflate 等，但基準只測單一情境"
tags: [rust, formal-verification, lean, llm-agents, spec-driven-development]
topics: [engineering.evals, agents.coding_agents]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## rust-djinn: You Should Specify Your Code Unambiguously (and Prove That You Did)

以 djinn! 巨集在 Rust 中寫規格，由 LLM 實作並經 Aeneas/Lean 證明後編譯。 **Why** 作者認為規格易寫錯或寫不完整，LLM 加驗證器可在不逐行審查程式碼下確保實作符合規格。 **How** cargo djinn implement 將規格轉為 Aeneas 的 proof obligation，啟動 LLM agent 撰寫程式並證明，再由 Lean 檢查；加入 unambiguity constraint 要求規格不容許實質不同的實作。 **What** 作者以 gzip 解壓為例，經 Codex 與 Claude Code 交替優化 100 輪，文中稱其略勝 zune_inflate 等測試過的實作，且未使用 unsafe 或 C 函式。

### 重點
- 流程：cargo djinn implement 一次完成翻譯成 Aeneas、啟動 LLM agent、驗證；cargo djinn optimize 以 benchmark 做 hillclimbing，效能不進步的版本會被丟棄
- unambiguity constraint：要求證明不存在與規格實質不同的實作，以抵抗規格遺漏（例如忘了輸出必須是輸入的排列）
- gzip 解壓：約 300 行規格（含壓縮），文中稱 rust-djinn 在純 safe Rust 中略勝 zune_inflate 等，但基準只測單一情境

**原文：** [lobsters-vibecoding](https://henniger.dev/post/djinn/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

rust-djinn: You Should Specify Your Code Unambiguously (and Prove That You Did)

Simon Henniger ( email me )

I have a program that grants wishes, as long as I can state them precisely. Instead of implementing a Rust function, I describe what it should do, and the Djinn writes code that provably does exactly that. Suppose I want to sort a list. I write:

My Djinn is not magic, but it is the manifestation of a dream. People have wanted something like this for a long time: humans write specifications, then have LLMs implement them and prove to a verifier that their implementations are correct. In theory, this LLM-verifier combination is powerful (thanks to the LLM), but still safe and reliable so you don't need to read the resulting code (thanks to the verifier). In practice, it's a bit harder than it sounds. While the verifier provides certainty that the LLM's code matches our specification, it’s easy to make specification errors or underspecify. Also, you have to set up verification software (and establish trust boundaries), juggle different languages, and babysit agents. For this to land, it needs to be tractable for normal SWEs, and currently, it’s a pain even for formal methods experts.

What if there was an easy way for everyone to write formal specs in a somewhat familiar format, use LLMs for code implementation and optimization, and mix the resulting code with their regular project? One that works even for those who don’t want to touch Lean code directly or who don’t trust themselves to write a perfect spec on the first attempt?

That’s the Djinn — more precisely, rust-djinn .

 Let’s build some tooling and a more pleasant syntax. 

My approach builds on Aeneas , which translates Rust into Lean (and other proof assistants) so you can prove theorems about the original Rust code.
Traditionally with Aeneas, we would write the specification in Lean. But that is not ideal — after all, we want our specified functions to tightly integrate with our existing Rust codebases.

That’s where rust-djinn comes in. It lets you specify a function within your existing Rust codebase using a djinn! macro. The Djinn has tooling that translates everything inside djinn! blocks into a Lean specification and implements it using an LLM. Within the blocks, you can use a subset of the normal Rust libraries and type system [1] . And once the LLM implementation is proven correct, it’s compiled and you can use the functions just like you would any other Rust code.

Within a djinn! block, the normal rules of imperative Rust programming don’t hold: we’re writing constraints. You can conceptualize the body as a long sequence of assert statements. Even the for loop is not an actual loop, but a universal quantifier (“for all items x in v, this constraint holds”). We write our code in a sort of relational programming language, constraining inputs and outputs. None of it is directly executable.

 How do we turn this into executable code? 

The tooling finds all djinn! blocks (which can be freely mixed into any Rust code base) and turns them into what we call “proof obligations” in Aeneas. A proof obligation is a theorem that must hold true about the (executable) code. With those proof obligations in hand, we spawn an LLM agent and ask it to (1) write Rust code that matches our spec, and (2) prove to us that it does so by fulfilling all proof obligations. We then ask Aeneas and Lean to check that our LLM’s proofs are correct, and finally we can compile the LLM’s Rust code with the regular Rust compiler.

This entire translation process happens in a single command: cargo djinn implement does everything from translation into Aeneas, spawning an LLM agent, babysitting it, and verifying that its work is correct. The programmer never has to touch Aeneas or Lean.

The newer LLMs are pretty good at this! They’re able to implement and prove even medium-sized specs of hundreds of lines (resulting in thousands of lines of code and much more in proofs) in a span of minutes to a few hours. Because we spawn an LLM agent, we can use the subscriptions (as opposed to API billing), making this remarkably cost-effective. And of course, we expect LLMs to get cheaper and better in the future.

Once we have the initial implementation, we make a benchmark for our measurements and run cargo djinn optimize . This optimizer is just an infinite loop that keeps spawning more and more agents which optimize the code. We can optimize for speed or for another target function: for instance, in compression, we also care about the compression factor. At every round of optimization, the agents need to prove their code is still correct and they need to demonstrate that it is faster on the benchmark. If it is not faster, it gets discarded, making this a classic instance of hillclimbing.

Within this framework, we can treat the LLM essentially as a compiler and we don’t have to review the code it wrote. We know what the spec is and we trust Lean to check it.

 Any Rust programmer should be able to easily learn rust-djinn. It completely encapsulates both the LLM implementer agent and Lean/Aeneas; there is no need for the programmer to ever touch either. It also comes with some built-in protections to ensure that Rust never accidentally compiles a stale implementation or one that doesn't verify.

 But what if we underspecify? 

Think back to all those genie stories you may have heard as a kid. Your djinn fulfills your wishes, but not in the way you want because you don’t express yourself accurately enough.

The same problem exists in programming. What if our spec is wrong? How confident are we in our ability to write a good spec? In general, the answer is not very, and this is called the “spec elicitation problem” (Max von Hippel and Quinn Dougherty write about it at length here ).

While bugs will always be a problem, a particular issue in this framework is actually underspecified code. What if we forget about something important? Suppose we forget to say that the output is a permutation of the input:

Now the function could always return a list of all zeros! Even if we trust the model to initially try to implement what we must have meant (which we probably shouldn’t), this kind of underspecification is a ticking time-bomb in an optimization loop.

 The Unambiguity Constraint 

What if your first wish for the Djinn could be: “for the following wishes, do what I mean, not what I say.” Well, it’s a bit unrealistic. The genie is powerful, but how would it know exactly what you want? Maybe you don’t even know yourself because you haven’t fully conceptualized it. So what if you could say: “challenge me to express myself unambiguously, so that you cannot misunderstand me anymore” ?

That’s what we’re doing! rust-djinn automatically includes a proof obligation for spec unambiguity. So the model not only has to prove that its implementation matches the spec, but also that no substantially different implementation [2] would. Thus we can be relatively certain that the LLM has no leeway; with the unambiguity constraint, the verifier becomes a strong version of AI control.

The constraint makes the Djinn reject our wrong underbaked sorting spec and accept the correct one above. It also leads to something akin to “fighting the borrow checker”: a spec novice will be fighting the unambiguity constraint. If the human developer ever gets bored, they can enlist an LLM’s help. Turns out they’re pretty good at helping with writing specs too (just carefully check the results!).

Because it’s so common to fight the unambiguity constraint, I built a little smoke check that quickly tests for unambiguity on part of the search space and offers a counterexample when it is violated. I put this in a linter-style IDE plugin and it’s pretty fun to use.

For more details on unambiguity, read the academic paper I co-wrote with Stephen Chong and Nada Amin on an earlier dialect of Djinn (which used Dafny instead of Aeneas, but the concepts have remained similar).

 Example: Gzip Spec 

With this, we can now:

A few weeks ago, Kim Morrison wrote a brilliant blog article about how Lean is faster than Rust . She wrote a spec for gzip in Lean and had an LLM optimize the code (using Lean to prove that every step was correct) until it was faster than a Rust implementation. Of course, lean-gzip is not perfect. Kim herself acknowledges that her approach worked less well on decompression: even Rust baseline miniz_oxide is ~1.5x faster (and another Rust library, zune_inflate, is even faster, ~2.4x). It also uses a lot of bespoke tooling that doesn’t generalize to other workloads.

Let’s see how our approach does. I’ll start with decompression.

Using some LLM help, I translated Kim’s spec into Djinn. It’s less than 300 lines (including compression) and you can read it here on GitHub .

Nothing in the spec gives any indication at all that this code will be fast. We describe things like extracting individual bits by calling 2.pow. But that doesn’t matter too much. Because the spec only describes the relationship between inputs and outputs, any two ways of writing it that are logically equivalent lead to the same implementations. Writing it the slow-looking way shouldn’t cost anything, as long as the LLM can prove that its faster code satisfies the spec.

Unlike Kim’s implementation, we also don’t add any external C or unsafe Rust functions for extra performance. Obviously, inline assembly and explicit vector instructions are also off-limits because Aeneas cannot verify them. We rely only on our LLM and the Rust compiler’s ability to optimize safe Rust code.

Given this spec, I used Codex and Claude Code (GPT 6 Astra at ultra and Fable 5.1 at xhigh) to optimize for 100 rounds (alternating between the two each round).

They optimized a bunch of stuff: 11-bit Huffman lookup tables built once per block, whole-token decoding from a single 64-bit bit window with packed table entries and the refill kept off the dependency chain, a pre-sized output buffer with unconditional 8-byte copy chunks, slice typing that lets LLVM drop bounds checks, and runtime-validated hints for long codes so proofs only need termination. They also tried a few things that didn't work: wider tables, branch-free or batched token decoding, overlapping-copy tricks for short distances, fusing literals into copies, out-of-line copies, and further polishing of the per-block setup.

And it turns out that the Djinn narrowly beats every other implementation [4] I tested so far (including zune_inflate, which claims to currently be the fastest safe Rust implementation):

Note that our headroom compared to libdeflate is fairly small and it could sometimes win depending on the dataset. Our benchmark also only tests a single setting (decoding a file that is already completely in memory), while the others are carefully constructed to support streaming. But that’s beside the point. The point isn’t to build a faster Gzip, but a verified Gzip in safe Rust that is no slower (or only insignificantly slower) than the fastest hand-optimized C implementation. [8] 

I also tried this on compression. Compared to Kim’s lean-gzip, rust-djinn reaches similar compression ratios but is a bit slower for low compression levels and faster for higher ones. See details on this and the optimization process here on GitHub .

 Next steps 

I’m pretty excited about this and I want to try more things!

 You can try rust-djinn yourself: https://github.com/shenniger/rust-djinn 

 This post is based on an academic paper I co-authored with Stephen Chong and Nada Amin. I am also grateful to Rhea Karty, Samuel Leßmann, and Max von Hippel for their comments. 

 Footnotes 

Mix specs into our normal Rust code

Spawn agents at the press of a button and have them implement the specs

Pretend our LLM is part of our compiler because we’ve verified everything it does and don’t need to read the code

Hillclimb to get the fastest-possible implementation (also at the press 

[... truncated for safety ...]

</details>