---
id: inbox_6c22ba12
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0053-lobsters-ai-the-need-for-a-formally-verifiable-mains-a4ff]]"
title: "The need for a formally verifiable mainstream programming language"
url: https://blainehansen.me/post/mainstream-verifiable-language/
source: lobsters-ai
published_at: 2026-11-26T14:06:50-06:00
fetched_at: 2026-11-27T01:04:26.218125+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "要讓 LLM 時代的軟體可靠，主流程式語言就得能被形式化驗證。 **Why** 作者認為 LLM 只是把原本草率的工程習慣加速到更快的速度，品質持續惡化，證明助理與 LLM 本身都不足以解決。 **How** 作者提出 Magmide 的務實路線：編譯到 WebAssembly GC、採用 Rust 式型別但不設借用檢查器、先用 SMT 驅動的 Liquid Types 與 Flow Effects，之後整合 Lean 作為證明層。 **What** 文中引用 Leonardo de Moura 的觀點：證明器只保證證明正確，仍需人閱讀定理陳述以確認其符合原意；作者因此放棄自建證明助理與組合語言層。"
key_points:
  - "正確性不等於正確的規格：證明通過後，仍需人確認 theorem statement 是否捕捉真正意圖"
  - "Magmide 新路線：WebAssembly GC 為編譯目標，先用 Liquid Types 與 Flow Effects，後期整合 Lean 與 Iris 式分離邏輯"
  - "作者棄用自建證明助理與組合語言層，理由是 Lean 進展快且組合語言採用門檻過高"
tags: [formal-verification, programming-language, magmide, llm-code-quality, lean]
topics: [engineering.architecture, security]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The need for a formally verifiable mainstream programming language

要讓 LLM 時代的軟體可靠，主流程式語言就得能被形式化驗證。

**Why** 作者認為 LLM 只是把原本草率的工程習慣加速到更快的速度，品質持續惡化，證明助理與 LLM 本身都不足以解決。

**How** 作者提出 Magmide 的務實路線：編譯到 WebAssembly GC、採用 Rust 式型別但不設借用檢查器、先用 SMT 驅動的 Liquid Types 與 Flow Effects，之後整合 Lean 作為證明層。

**What** 文中引用 Leonardo de Moura 的觀點：證明器只保證證明正確，仍需人閱讀定理陳述以確認其符合原意；作者因此放棄自建證明助理與組合語言層。

### 重點
- 正確性不等於正確的規格：證明通過後，仍需人確認 theorem statement 是否捕捉真正意圖
- Magmide 新路線：WebAssembly GC 為編譯目標，先用 Liquid Types 與 Flow Effects，後期整合 Lean 與 Iris 式分離邏輯
- 作者棄用自建證明助理與組合語言層，理由是 Lean 進展快且組合語言採用門檻過高

**原文：** [lobsters-ai](https://blainehansen.me/post/mainstream-verifiable-language/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

To save software engineering from LLMs, we need a mainstream verifiable language

The culture of software engineering has to change, and that will take many different projects to achieve.

§ The long winding road of Magmide

§ Nothing will save us but us

published: June 21, 2026 - last updated: July 24, 2026

Because of LLMs, the discipline of software engineering is in crisis. Quality is nose-diving , and I see no reason why it won't keep getting worse. Software engineering was struggling before LLMs (opens new window) . The default was to be sloppy and poorly considered, and now everyone is frantically accelerating those same terrible practices to LLM speed.

Something has to change. I've been preoccupied with this for a while (opens new window) , but much more qualified people finally fully agree with me (opens new window) . The only way forward is to fully embrace formal verification (opens new window) , all the way down to the foundations of our civilizational software stack. We have to post-hoc verify the things we can, and rewrite the rest.

But that's easier said than done. Existing formal verification tools suffer from massive usability (opens new window) and understandability (opens new window) problems, and have failed to make any kind of noticeable impact on the broader culture of software engineering.

It might be tempting to say that LLMs will actually save us in this regard, by allowing humans to create formally verified code without needing to understand its fundamentals in any way. This is pure cope. Merely having excellent proof assistants and LLMs will never be good enough. Even in a world where something like Lean is extremely scalable and LLMs can write all proofs, it doesn't matter if they aren't adopted by actual industry engineers as they build the real apps we actually use. For provably correct code to defend us from the LLM future:

Proof assistants guarantee that proofs are correct, but correctness alone is not enough. Someone has to read the theorem statements and confirm they capture the intended mathematics. This is the human contract that no amount of automation can eliminate.

This is what most voices are missing in this discussion: a safe future isn't going to be delivered by a small priestly class of formal methods researchers, too much code must be produced in too many contexts. The entire discipline of software engineering has to grow up and demand that all code we produce is at minimum provably safe. This requires many different projects and bets that attack this imperative of cultural change from different directions.

My chosen angle is Magmide, a project whose goal is to create a new formally verifiable programming language intended for immediate adoption by practitioners. However when I first had this idea my specific plan was woefully over-ambitious and unrealistic, since I wanted to make a whole new proof assistant and an assembly-level base language so the system could be verified all the way down to the metal.

I pursued it for a time as a startup, and I met with some investors and was applying for an SBIR grant. Then I realized some obvious problems with my approach (opens new window) :

So now after a few years pursuing other projects and letting all these ideas marinate, I've arrived at a much simpler and more pragmatic vision of what Magmide could be. If I started working on it today, it would:

This design is specifically intended to appeal to actual engineers and "meet them where they are". The roadmap would start from a simpler more mainstream design and go "bottom up" by adding more and more proving capabilities, rather than going "top down" by starting with the most formally powerful system and then seeking to make it more usable.

A possible analogue for the adoption of Magmide is Deno (opens new window) : Deno is "just javascript/typescript", but it adds a runtime layer of permissions checking. Engineers who care about sandbox safety have enthusiastically adopted Deno, and Flow Effects would offer strictly more security.

I continue to stand behind basically all the arguments I made in the Magmide repo (opens new window) (aside from the specific architecture). Formal verification must become the mainstream of software engineering, and we have to embrace a wide diversity of approaches to make that happen. Software engineers aren't a monolith, and not every cultural pocket will respond to the same new tools and resources.

And you know what, LLMs will probably help a lot! But we can't just wait around for an all-knowing machine god to save us from ourselves. If we bet our whole future on ASI making all our problems go away and then that doesn't happen (opens new window) , history will look back on us even more foolish and disastrous than all the millennialists (opens new window) who merely wasted their own time and resources.

It is our responsibility to meet the challenges of our age with full agency and responsibility, and treat the emergence of a beneficent super-intelligence as an improbable jackpot.

It needs to be possible to formally verify code that runs in any environment, from web browsers down to embedded systems.

Industry engineers need to know provably correct code is even possible and be comfortable enough with it to at least tell their LLMs to write it.

Those industry engineers must be able to reason about formal correctness properties enough to even know the right things are being proven . In the words of Leonardo de Moura (opens new window) : Proof assistants guarantee that proofs are correct, but correctness alone is not enough. Someone has to read the theorem statements and confirm they capture the intended mathematics. This is the human contract that no amount of automation can eliminate.

It didn't make sense to build a new proof assistant when Lean has been making such rapid progress.

An assembly-level language was insanely difficult and wasn't necessary to gain adoption from practitioners.

I didn't have the appetite to pursue some strained business model for a project that ultimately makes most sense as a pure public good.

Compile to WebAssembly using the Garbage Collection (opens new window) features.

Have a Rust-inspired type system but without the difficulties of the borrow-checker.

Start with basic and more easily learnable SMT powered (opens new window) Liquid Types (opens new window) and Flow Effects (opens new window) .

Over time integrate Lean as the proof layer, and use some separation logic paradigm like Iris (opens new window) to bootstrap the language and verify its own implementation.

</details>