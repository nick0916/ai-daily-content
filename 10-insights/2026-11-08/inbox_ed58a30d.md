---
id: inbox_ed58a30d
date: 2026-11-08
source_ref: "[[00-inbox/2026-11-08/2348-medium-tag-llm-why-think-step-by-step-buys-an-ai-more-c-6fe0]]"
title: "Why “Think Step by Step” Buys an AI More Compute, Not More Intelligence"
url: https://medium.com/@mahdi.nasermoghadasi/why-think-step-by-step-buys-an-ai-more-compute-not-more-intelligence-8f47ce312ebe?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-08T15:36:02+00:00
fetched_at: 2026-11-08T23:54:01.194691+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Chain-of-thought 是用更多 token 換取更多運算，而不是增加模型智力。 **Why** 語言模型每個 token 的運算量固定，要讓它「想久一點」，只能讓它寫更多內容。 **How** 透過產出更多中間推理 token，增加整體運算量。 **What** 原文為概念性說明，未提供實驗數據或具體模型名稱。"
key_points:
  - "模型每個 token 的運算量固定，「想更久」等同於寫更多 token"
  - "原文主張 step-by-step 增加的是運算量，而非智力"
  - "原文未提供實驗數據或基準測試"
tags: [chain-of-thought, test-time-compute, reasoning, llm-internals]
topics: [engineering.inference]
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Why “Think Step by Step” Buys an AI More Compute, Not More Intelligence

Chain-of-thought 是用更多 token 換取更多運算，而不是增加模型智力。

**Why** 語言模型每個 token 的運算量固定，要讓它「想久一點」，只能讓它寫更多內容。

**How** 透過產出更多中間推理 token，增加整體運算量。

**What** 原文為概念性說明，未提供實驗數據或具體模型名稱。

### 重點
- 模型每個 token 的運算量固定，「想更久」等同於寫更多 token
- 原文主張 step-by-step 增加的是運算量，而非智力
- 原文未提供實驗數據或基準測試

**原文：** [medium-tag-llm](https://medium.com/@mahdi.nasermoghadasi/why-think-step-by-step-buys-an-ai-more-compute-not-more-intelligence-8f47ce312ebe?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A language model spends the same fixed effort on every token it writes, so the only way to make it think longer is to let it write more. Continue reading on Medium »

</details>