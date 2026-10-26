---
id: inbox_12c24d4e
date: 2026-10-25
source_ref: "[[00-inbox/2026-10-25/0249-medium-tag-llm-tokens-before-words-what-an-ai-model-act-b4e9]]"
title: "Tokens Before Words: What an AI Model Actually Receives"
url: https://medium.com/@mizcausevic/tokens-before-words-what-an-ai-model-actually-receives-68b865e76631?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-25T21:11:11+00:00
fetched_at: 2026-10-26T02:58:04.294111+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "模型看到的是 token 整數序列，而非原始文字。 **What** 文章探討 token 的切分位置，以及 token 數量為何會因語言與 tokenizer 而異；節錄未給具體數字。"
key_points:
  - "模型接收的是 token 整數序列，而非原始句子"
  - "同一段文字的 token 數量因語言與 tokenizer 而異"
  - "節錄未提供具體切分範例或數字"
tags: [tokenizer, tokens, llm-internals, cost-estimation]
topics: [engineering.inference]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Tokens Before Words: What an AI Model Actually Receives

模型看到的是 token 整數序列，而非原始文字。 **What** 文章探討 token 的切分位置，以及 token 數量為何會因語言與 tokenizer 而異；節錄未給具體數字。

### 重點
- 模型接收的是 token 整數序列，而非原始句子
- 同一段文字的 token 數量因語言與 tokenizer 而異
- 節錄未提供具體切分範例或數字

**原文：** [medium-tag-llm](https://medium.com/@mizcausevic/tokens-before-words-what-an-ai-model-actually-receives-68b865e76631?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Your sentence becomes a list of integers before the model sees it. See where the cuts fall, why counts differ by language and by tokenizer&#x2026; Continue reading on Medium »

</details>