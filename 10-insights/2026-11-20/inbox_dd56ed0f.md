---
id: inbox_dd56ed0f
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0047-latent-space-the-war-against-slop-and-an-emerging-wea-db5e]]"
title: "The War Against Slop and an Emerging Weapon to Fight it: Formal Verification"
url: https://latent.space/p/formal-verification/
source: latent-space
published_at: 2026-11-20T21:18:41+00:00
fetched_at: 2026-11-21T00:53:03.129772+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用數學證明檢查 AI 寫的程式，取代「測了沒問題就算過」。 **Why** AI 生成的程式碼越來越多，「slop」成了工程師每天的顧慮；測試、掃描、讓另一個模型評審都無法確定問題是否找完了。 **How** AI 負責寫證明，Lean 這類證明助手逐步檢查每一步，結果就不依賴 AI 是否正確；&Truth 想打造能讀任何語言程式碼、證明其符合明確規格的「verification machine」。 **What** 文章介紹 &Truth（共同創辦人 Clark Barrett，cvc5 共同作者）、Harmonic（Aristotle）、Theorem、Axiom Math（AxiomProver、AXLE）等公司。Anthropic 與 Theorem 的文章指出，在 36 個小型驗證任務上，Opus 5.5 達到 50% 解題率，使用的 token 比 Opus 5 少約 40%。"
key_points:
  - "測試、修補、掃描的限制是無法確定「是否已找完所有問題」；形式驗證的差異在於能知道何時完成（Barrett 的說法）"
  - "Anthropic 回報：36 個小型驗證任務上，Opus 5.5 以約少 40% token 達到 50% 解題率（相較 Opus 5），形式驗證雖然 token 昂貴但正變得更省"
  - "&Truth 的首要用例是掃描全球 C 程式碼確認記憶體安全；開發流程從 vibe-coding 轉向「veri-coding」，人把更多時間花在寫 spec 與 review"
tags: [formal-verification, lean, slop, veri-coding, memory-safety]
topics: [engineering.evals, security, agents.coding_agents]
importance: 3
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The War Against Slop and an Emerging Weapon to Fight it: Formal Verification

用數學證明檢查 AI 寫的程式，取代「測了沒問題就算過」。

**Why** AI 生成的程式碼越來越多，「slop」成了工程師每天的顧慮；測試、掃描、讓另一個模型評審都無法確定問題是否找完了。

**How** AI 負責寫證明，Lean 這類證明助手逐步檢查每一步，結果就不依賴 AI 是否正確；&Truth 想打造能讀任何語言程式碼、證明其符合明確規格的「verification machine」。

**What** 文章介紹 &Truth（共同創辦人 Clark Barrett，cvc5 共同作者）、Harmonic（Aristotle）、Theorem、Axiom Math（AxiomProver、AXLE）等公司。Anthropic 與 Theorem 的文章指出，在 36 個小型驗證任務上，Opus 5.5 達到 50% 解題率，使用的 token 比 Opus 5 少約 40%。

### 重點
- 測試、修補、掃描的限制是無法確定「是否已找完所有問題」；形式驗證的差異在於能知道何時完成（Barrett 的說法）
- Anthropic 回報：36 個小型驗證任務上，Opus 5.5 以約少 40% token 達到 50% 解題率（相較 Opus 5），形式驗證雖然 token 昂貴但正變得更省
- &Truth 的首要用例是掃描全球 C 程式碼確認記憶體安全；開發流程從 vibe-coding 轉向「veri-coding」，人把更多時間花在寫 spec 與 review

**原文：** [latent-space](https://latent.space/p/formal-verification/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The word of the year in the AI industry over 2026 has been “slop” — meaning low-quality output from a large language model. And with so much code being AI-generated now, avoiding slop has become a daily concern for software engineers. So how to do that? One way is to use formal verification systems , which use mathematical proofs and logic to verify the correctness of software or hardware. With AI’s growing prowess at solving math problems , there’s now a number of AI companies offering formal verification systems. They include Harmonic , Theorem , Axiom Math , and a new entrant called &Truth (pronounced ‘and truth’). In this article we’ll look at some of the approaches these companies are taking. How formal verification is used in software and AI today In order to better understand the landscape of formal verification systems, we spoke to one of its leading proponents: Clark Barrett , &Truth’s co-founder and co-CEO. He’s also Corbel Professor (Research) of Computer Science at Stanford and was the co-creator of cvc5 , a popular automated reasoning engine used in formal verification. Without getting too in the weeds, cvc5 is what’s called a “solver” for satisfiability modulo theories (SMT) , which Barrett says is widely used in companies like Amazon. For instance, cvc5 is used for specification analysis and test generation in Kiro , Amazon’s agentic development environment. “It's been fun to see my tools go from a good idea in the lab to cvc5 is now called billions of times a day in production pipelines at Amazon,” Barrett told us. Via a 2022 paper about cvc5 co-authored by Clark Barrett. When AI coding agent companies talk about “verifying” their work, it typically means agents running tests, critiquing their own output, or having another AI model judge it. So I asked Barrett how far short of real verification does that fall? “The main difference is really just, how do you know when you're done,” he replied. “So if you're testing, patching, scanning — using all these existing tools — they're quite good. I mean, they find a ton of problems. They raise those issues. But you're never quite sure, did I find all of them [the issues] or is there one more lurking there that my tool can't find?” &Atlas, the first tool of &Truth; it’s “a map of the world’s open-source code, starting with code written in the C programming language.” Lean’s role in formal verification &Truth builds on Lean , an open-source programming language and proof assistant . The company combines AI with automated reasoning techniques to construct proofs that Lean can check. Lean is a language used by frontier models to solve all manner of supremely difficult math problems . For instance, just this week GPT-6.2 Astra produced what Vals believes is “the first Lean proof of Smoktunowicz’s Gap Theorem.” Vals added that Anthropic also used Lean to formalize Fermat’s Last Theorem, a project of 13 million lines. The latest big math news is a report that Anthropic mathematician Levent Alpöge claims he used Claude to prove the 167-year-old Riemann hypothesis — and he posted the proof in Lean . Example of Lean code; via Lean project website &Truth is building what it calls a “verification machine” on top of the Lean framework, with the ambition of reading code “in any language, proving whether it satisfies precisely stated requirements , and enabling humans to trust it without having to understand every line.” “What Lean does is it just checks that you didn't make a mistake,” explained Barrett. “So you can think of it as a very sophisticated checker for mathematics.” This has implications for model training too. Axiom Math uses formal verification to provide correctness feedback for training its mathematical reasoning systems, with proof attempts helping improve future models. In an interview with Latent Space in June , Axiom CEO Carina Hong made the point that formal verification — and what Lean enables — isn’t just a defensive measure. “Formal verification, or verified AI, to us it's not just about handling or kicking out the lousiness, the hallucinations, the mistakes. It's about scaling brilliance. It's about super-intelligence.” Axiom develops AxiomProver , an AI system that generates Lean proofs, alongside AXLE , its toolkit for exploring, validating, and manipulating those proofs. Harmonic’s Aristotle , an “ automated theorem prover ”, uses Lean heavily in its offering. “Inside Aristotle, AI writes the proofs and Lean checks every step of them, so a result never rests on the AI being right,” states the company on its website. Harmonic’s workflow Cybersecurity and LLM-scaled formal verification Given the heightened level of paranoia about cybersecurity these days — some might say in the days leading up to AGI — formal verification systems seem like they’re needed more than ever. And Barrett confirmed that cybersecurity is a key focus for &Truth. “One really powerful use case for our technology is going through all the C code in the world, whether it be open source or closed source, and trying to ensure that it's memory safe. And then if it's not memory safe, we can point to: here's a problem with this piece of code, you need to fix it so that it's safe.” Security is also a focus of Theorem , one of &Truth’s competitors. “Verification is the only defense that holds while adversaries scale,” Theorem states on its homepage. Theorem’s proof-efficiency eval : “KB of machine code verified per hour on our proof-efficiency eval, by model release date, with 95% intervals.” Theorem has also collaborated with Anthropic on this topic, resulting in a blog post entitled “ LLMs are making formal software verification feasible at a much larger scale .” One of the more encouraging notes in the post is that formal verification, although currently token-expensive, is starting to get more token-efficient. On a set of 36 small verification tasks, Anthropic reported that Opus 5.5 reached a 50% solve rate using about 40% fewer tokens than Opus 5. This trend is expected to continue as more models are “trained on long verification tasks.” Theorem and Anthropic describe “LLM-scaled formal verification” as a promising approach to providing security guarantees at a previously impractical scale. Anthropic diagram: “from code to a machine-checked guarantee”; in this case using Rocq rather than Lean. The “veri-coding” experience for developers Lastly, how does formal verification fit into a developer’s workflow? On its website, &Truth states that developers will move from vibe-coding to “veri-coding” — meaning the verification layer is part of the workflow. “If you've got your verification machine connected to your agent, you can still say, ‘hey, I want you to build this,’ said Barrett. “Maybe there's a little bit of work to really nail down with the agent what the specification is of what you want to build. But then the agent can go under the hood, collaborate with the formal [verification] tool, and essentially what you'll see is almost no difference except your code will work the first time.” The idea, then, is that more of the developer’s time will be spent on spec writing and reviewing than on coding or reviewing code. Verify all the outcomes While I was finishing up this article, I came across this tweet by Cognition dev rel Nader Dabit: Whether the term “outcome engineering” sticks or not, he’s onto something in terms of where we are with coding. When you just tell your team of agents what you want and they go ahead and build it, you (the human developer) need a way to check the correctness of what your agents deliver. If companies like &Truth, Harmonic, Theorem and Axiom Math have their way, formal verification could become an increasingly practical way to check those outcomes.

</details>