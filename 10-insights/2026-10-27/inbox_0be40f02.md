---
id: inbox_0be40f02
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/2337-infoq-main-cloudflare-and-voidzero-introduce-tsrs-a-a97c]]"
title: "Cloudflare and VoidZero Introduce tsrs: An AI-Generated Rust Port of TypeScript"
url: https://www.infoq.com/news/2026/10/cloudflare-tsrs-ai-typescript/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-27T07:34:00+00:00
fetched_at: 2026-10-27T23:45:46.851035+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 AI 產生的 Rust 重寫版 TypeScript 型別檢查器，目標是更快、更省記憶體。 **What** Cloudflare、VoidZero 與 Max Schwenk 發表實驗性的 tsrs，為 TypeScript 編譯器的 Rust 移植版，開發過程有 TypeScript 團隊參與。Cloudflare 宣稱型別檢查最高比 TypeScript 7.0 快 8 倍、記憶體少 70%，但對 7.1 beta 的一項測試只快 2.7 倍。目前缺少 watch 模式與 language server，遇到型別錯誤時以 exit code 2 結束。"
key_points:
  - "宣稱檢查速度最高為 TypeScript 7.0 的 8 倍、記憶體減少 70%；對 7.1 beta 的一項測試僅 2.7 倍"
  - "與 TypeScript 團隊合作，由 Cloudflare、VoidZero、Max Schwenk 發表，屬實驗性質"
  - "尚無 watch 模式與 language server；型別錯誤時 exit code 為 2"
tags: [tsrs, typescript, rust, ai-generated-code, cloudflare]
topics: [agents.coding_agents, product_and_org.product]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare and VoidZero Introduce tsrs: An AI-Generated Rust Port of TypeScript

用 AI 產生的 Rust 重寫版 TypeScript 型別檢查器，目標是更快、更省記憶體。

**What** Cloudflare、VoidZero 與 Max Schwenk 發表實驗性的 tsrs，為 TypeScript 編譯器的 Rust 移植版，開發過程有 TypeScript 團隊參與。Cloudflare 宣稱型別檢查最高比 TypeScript 7.0 快 8 倍、記憶體少 70%，但對 7.1 beta 的一項測試只快 2.7 倍。目前缺少 watch 模式與 language server，遇到型別錯誤時以 exit code 2 結束。

### 重點
- 宣稱檢查速度最高為 TypeScript 7.0 的 8 倍、記憶體減少 70%；對 7.1 beta 的一項測試僅 2.7 倍
- 與 TypeScript 團隊合作，由 Cloudflare、VoidZero、Max Schwenk 發表，屬實驗性質
- 尚無 watch 模式與 language server；型別錯誤時 exit code 為 2

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/cloudflare-tsrs-ai-typescript/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare, VoidZero and Max Schwenk announced tsrs, an experimental Rust port of the TypeScript compiler, built with the TypeScript team's involvement. Cloudflare claims up to 8x faster checking and 70% less memory than TypeScript 7.0, though one test against 7.1 beta showed 2.7x. It lacks watch mode and a language server, and exits with code 2 on type errors. By Daniel Curtis

</details>