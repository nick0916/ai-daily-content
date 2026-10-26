---
id: inbox_807b81ef
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/2338-hackernews-slopcodebench-10-2026-opus-5-5-astra-win-f558]]"
title: "SlopCodeBench 10/2026 – Opus 5.5, Astra wins overall, xhigh considered harmful"
url: https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/benchmarking-new-models-on-slop-code-bench.md
source: hackernews
published_at: 2026-10-15T19:09:34+00:00
fetched_at: 2026-10-21T23:42:51.140644+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用一連串事先不透露的功能需求，測試 AI 寫程式能否在同一份程式碼上持續累積而不爛掉。 **Why** 多數 benchmark 都是一次性任務，爛程式碼不會拖累後續進度，與真實軟體開發不符。 **How** SlopCodeBench 讓模型面對逐步揭露的功能清單（checkpoints），每個 checkpoint 沿用前一階段留下的同一份 codebase，所以前面寫出的 slop 會影響之後的進展。 **What** 這是 2026 年 10 月的更新，標題寫 Opus 5.5、Astra 總體勝出、「xhigh considered harmful」；input 僅含 benchmark 介紹，未提供具體分數或 xhigh 的細節，其餘無法確定。"
key_points:
  - "SlopCodeBench 採 checkpoint 機制：功能需求逐步揭露、模型事先不知道，且同一 codebase 貫穿單一多階段挑戰"
  - "設計重點是讓早期的 slop code 會拖累後續進度，比一次性任務 benchmark 更接近真實開發"
  - "標題稱 Opus 5.5 納入測試、Astra 總體勝出、xhigh 設定被認為有害；但 input 沒有具體數字，細節無法確定"
tags: [slopcodebench, coding-benchmark, context-engineering, humanlayer, evals]
topics: [engineering.evals, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## SlopCodeBench 10/2026 – Opus 5.5, Astra wins overall, xhigh considered harmful

用一連串事先不透露的功能需求，測試 AI 寫程式能否在同一份程式碼上持續累積而不爛掉。

**Why** 多數 benchmark 都是一次性任務，爛程式碼不會拖累後續進度，與真實軟體開發不符。

**How** SlopCodeBench 讓模型面對逐步揭露的功能清單（checkpoints），每個 checkpoint 沿用前一階段留下的同一份 codebase，所以前面寫出的 slop 會影響之後的進展。

**What** 這是 2026 年 10 月的更新，標題寫 Opus 5.5、Astra 總體勝出、「xhigh considered harmful」；input 僅含 benchmark 介紹，未提供具體分數或 xhigh 的細節，其餘無法確定。

### 重點
- SlopCodeBench 採 checkpoint 機制：功能需求逐步揭露、模型事先不知道，且同一 codebase 貫穿單一多階段挑戰
- 設計重點是讓早期的 slop code 會拖累後續進度，比一次性任務 benchmark 更接近真實開發
- 標題稱 Opus 5.5 納入測試、Astra 總體勝出、xhigh 設定被認為有害；但 input 沒有具體數字，細節無法確定

**原文：** [hackernews](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/benchmarking-new-models-on-slop-code-bench.md)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Quick update here since a lot of folks asked about what slopcodebench is &#x2F; where it fits in Slop code bench is unique among benchmarks in that it makes a model work against a progressively disclosed list of features (checkpoints) that it doesn’t know it advance, inheriting the same codebase through the lifecycle of a single multi-checkpoint challenge I like this because it much more mirrors how real software dev happens, rather than most benchmarks with one off tasks where slop code doesn’t hinder future progress The original post[1] and the SOL&#x2F;fable follow up[2] went into a bit more detail on the benchmark and its challenges 1. https:&#x2F;&#x2F;news.ycombinator.com&#x2F;item?id=49076391 2. https:&#x2F;&#x2F;github.com&#x2F;humanlayer&#x2F;advanced-context-engineering-f...

</details>