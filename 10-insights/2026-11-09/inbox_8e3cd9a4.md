---
id: inbox_8e3cd9a4
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2341-medium-tag-llm-why-the-same-prompt-gives-different-answ-5cee]]"
title: "Why the Same Prompt Gives Different Answers: Temperature, Sampling and Non-Determinism in LLM..."
url: https://anujaneja.medium.com/why-the-same-prompt-gives-different-answers-temperature-sampling-and-non-determinism-in-llm-bf08852f83e2?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-09T15:18:58+00:00
fetched_at: 2026-11-10T00:08:00.672182+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "同一個 prompt 每次答案不同，是採樣機制造成的，temperature 設為 0 也不保證可重現。 **Why** 模型輸出是依機率逐步取樣，並非固定對應。 **How** 原文說明 sampling、temperature 與 top-p 如何把機率分布轉成文字，並討論測試與設計方法。 **What** 文章指出即使 temperature 為 0 仍非完全可重現，因此 LLM 系統的測試需要容忍非確定性。"
key_points:
  - "temperature 0 仍不保證輸出可重現"
  - "sampling、temperature、top-p 決定機率分布如何轉為 token"
  - "文章討論非確定性下的測試與設計方法（原文摘要未列出具體做法）"
tags: [sampling, temperature, non-determinism, llm-testing]
topics: [engineering.evals, engineering.inference]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Why the Same Prompt Gives Different Answers: Temperature, Sampling and Non-Determinism in LLM...

同一個 prompt 每次答案不同，是採樣機制造成的，temperature 設為 0 也不保證可重現。

**Why** 模型輸出是依機率逐步取樣，並非固定對應。

**How** 原文說明 sampling、temperature 與 top-p 如何把機率分布轉成文字，並討論測試與設計方法。

**What** 文章指出即使 temperature 為 0 仍非完全可重現，因此 LLM 系統的測試需要容忍非確定性。

### 重點
- temperature 0 仍不保證輸出可重現
- sampling、temperature、top-p 決定機率分布如何轉為 token
- 文章討論非確定性下的測試與設計方法（原文摘要未列出具體做法）

**原文：** [medium-tag-llm](https://anujaneja.medium.com/why-the-same-prompt-gives-different-answers-temperature-sampling-and-non-determinism-in-llm-bf08852f83e2?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How sampling, temperature and top-p turn probabilities into text, why even temperature 0 isn’t reproducible, and how to test and design... Continue reading on Medium »

</details>