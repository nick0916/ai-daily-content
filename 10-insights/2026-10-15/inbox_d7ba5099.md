---
id: inbox_d7ba5099
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0102-lobsters-vibecoding-sunsetting-decomp-dev-1c7d]]"
title: "Sunsetting decomp.dev"
url: https://decomp.dev/
source: lobsters-vibecoding
published_at: 2026-10-15T08:27:41-05:00
fetched_at: 2026-10-25T01:28:46.812517+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "decomp.dev 停止新增專案與主索引，因排行榜機制讓刷進度與惡意行為變多。 **Why** 作者認為公開索引與排行榜在 AI 能快速產出後，鼓勵只追數字的行為，弊多於利。 **What** 網站 2024 年成立，既有專案頁與歷史資料保留，主索引與新增專案功能停用；作者列出惡意 fork 以 AI 補完、搶先釋出半成品 PC port，以及把 decompilation 與 port 混為一談等問題，且網站程式碼沒有開源授權。"
key_points:
  - "作者指出 Opus 4.6、GPT-5.4（2026 年初）與 GPT-6-Astra 讓 AI 能協助 matching decompilation，但仍需人工清理與審查作弊式結果"
  - "列舉三種濫用：惡意 fork 以 AI 補完專案、搶先釋出半成品 port、把 decompilation 與 PC port 混為一談"
  - "網站程式碼保留所有權利，明確禁止任何複製版使用其程式碼"
tags: [decompilation, video-game-preservation, community-governance, ai-slop, leaderboards]
topics: [product_and_org.adoption, security]
importance: 4
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Sunsetting decomp.dev

decomp.dev 停止新增專案與主索引，因排行榜機制讓刷進度與惡意行為變多。

**Why** 作者認為公開索引與排行榜在 AI 能快速產出後，鼓勵只追數字的行為，弊多於利。

**What** 網站 2024 年成立，既有專案頁與歷史資料保留，主索引與新增專案功能停用；作者列出惡意 fork 以 AI 補完、搶先釋出半成品 PC port，以及把 decompilation 與 port 混為一談等問題，且網站程式碼沒有開源授權。

### 重點
- 作者指出 Opus 4.6、GPT-5.4（2026 年初）與 GPT-6-Astra 讓 AI 能協助 matching decompilation，但仍需人工清理與審查作弊式結果
- 列舉三種濫用：惡意 fork 以 AI 補完專案、搶先釋出半成品 port、把 decompilation 與 PC port 混為一談
- 網站程式碼保留所有權利，明確禁止任何複製版使用其程式碼

**原文：** [lobsters-vibecoding](https://decomp.dev/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Sunsetting decomp.dev

What happens now?

Can I fork and host my own version of decomp.dev?

Why not just forbid AI-assisted projects?

decomp.dev was born in 2024 as a way to centralize matching decompilation progress and to help expand a community of talented, like-minded folks.

Historically, matching decompilation has been a brutally difficult, time consuming task, on the scale of years for any moderately-sized game with a number of active contributors. As we developed better tooling and shared knowledge around the intricacies of decompilation, the compilers, and the games themselves, progress began to accelerate.

AI's use in decompilation has been experimented with for years, with mixed results. Starting with the release of Opus 4.6 and GPT-5.4 in early 2026, it was clear that the models were being trained on matching decompilation (they appeared to know our specific tools and how to use them without explicit guidance), and could achieve decent results inside of an established, clean codebase with exhaustive documentation. However, those results still required a significant amount of human cleanup and fixes for obvious issues or cheating (code that technically compiles to the same machine code, but could not be reasonably passed as what the original developers wrote), and the cost per task was prohibitively expensive relative to the results.

Recent models (like GPT-6-Astra) shifted things even further: they are significantly better at following complex directions, cross-referencing resources for symbols or debug information, and writing natural code with enough guidance. They are also exceptionally good permuters: they can write small scripts that test many different source code forms and combinations to find a match, even across files and headers to cover aspects like inlined helpers, signature changes, and operation ordering. In addition, their ability to remain coherent and focused across long-horizon tasks allows them to work continuously without going off the rails. Finally, they can achieve these better results faster and cheaper than earlier models could.

It is now clear that, with the right guidance, human input, and code reviews, AI can expedite the decompilation process in a significant way. What is also now clear is that the community aspect of decompilation has been broken. Our projects have always been open source to encourage contributions and to benefit the community as a whole. Bad actors have been abusing this in increasingly troublesome ways:

decomp.dev was originally designed to gamify decompilation: watching the progress go up was a fun way to stay motivated when every fraction of a percent took real human effort. Today, that same idea has warped decompilation into a hollow numbers game, exacerbated by folks who just want to burn tokens to make number go up or "port game to PC", all else be damned. While the increased attention has brought in genuine folks who want to learn and contribute meaningfully, I believe that decomp.dev serving as a public index and leaderboard is now causing more harm than good.

decomp.dev will continue to track existing projects and serve individual project pages and historical data, but the main index and adding new projects are disabled.

No. decomp.dev's repository has never had an open source license, and I continue to reserve all rights to the (entirely human written) code. Any replica must not use decomp.dev's code in any form.

I have long held the opinion that AI is not the issue by itself, and we now know it can help tremendously when used correctly. "Slop" comes in many forms, is hard to define, and even harder to moderate. As a sole hobbyist, I don't have the energy (or desire) to define what makes a "good" decompilation and enforce that consistently across the hundreds of projects on the site.

As this era of decompilation comes to a close, I want to thank everyone who's been involved and contributed to our projects, communities and tools. The people and passion behind these projects have always been what's made them fun and rewarding.

— @encounter

Forking existing decompilation projects to "finish" them with AI. Every project works differently: some may not want to use AI for legal or ethical reasons, and others may be okay with AI, or use AI themselves, but do not want drive-by contributions from folks who have put no effort into making sure the contributions are good. The bottom line is that these kinds of hostile forks put little to no effort into meaningfully contributing to existing projects, tearing apart our community fabric.

Racing to port games, especially utilizing decompilations that they did not contribute to. Yes, now anyone with an AI subscription can manage to create a port or static recompilation that functions at a basic level. Compared to the decompilation process itself, porting is relatively easy, especially with the established tools written by talented humans. While community members put in the effort to decompile a game, opportunists have frequently raced to release a half-baked, barely-functional port from it.

Conflating decompilation and ports. For years, decompilation communities attempted to establish that decompilation is primarily for research: we love these games and want to understand how they work, and to uncover the mysteries that the original developers left behind. That's not to say that ports aren't fun too; they're just not the sole reason a decompilation exists. Sloptubers and subreddits like /r/decomps have done immense damage here, freely using "decomp" to mean "PC port".

</details>