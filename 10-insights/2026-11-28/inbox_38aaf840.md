---
id: inbox_38aaf840
date: 2026-11-28
source_ref: "[[00-inbox/2026-11-28/0142-medium-tag-llm-most-of-the-bill-is-remembering-e98c]]"
title: "Most of the Bill Is Remembering"
url: https://medium.com/@dydrnsj/most-of-the-bill-is-remembering-1dd3626c22da?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-28T00:56:38+00:00
fetched_at: 2026-11-28T01:53:39.192117+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "寫程式的 agent 成本多半花在重複讀取既有 context，而非新內容。 **What** 原文引用生產環境 trace：coding agent 單次請求的 input tokens 中位數約 129,000，其中約 500 為新內容。"
key_points:
  - "生產 trace 中，coding agent 單次請求的 input tokens 中位數約 129,000"
  - "其中約 500 tokens 為新內容，其餘為既有 context 的重複讀取"
  - "標題點出多數費用來自「記憶」（重複的 context），摘要未提供解法"
tags: [token-cost, context-window, coding-agents, production-traces, inference-cost]
topics: [agents.coding_agents, engineering.inference]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Most of the Bill Is Remembering

寫程式的 agent 成本多半花在重複讀取既有 context，而非新內容。

**What** 原文引用生產環境 trace：coding agent 單次請求的 input tokens 中位數約 129,000，其中約 500 為新內容。

### 重點
- 生產 trace 中，coding agent 單次請求的 input tokens 中位數約 129,000
- 其中約 500 tokens 為新內容，其餘為既有 context 的重複讀取
- 標題點出多數費用來自「記憶」（重複的 context），摘要未提供解法

**原文：** [medium-tag-llm](https://medium.com/@dydrnsj/most-of-the-bill-is-remembering-1dd3626c22da?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The median request from a coding agent in a production trace carries about 129,000 input tokens. Roughly 500 of them are new. Continue reading on Medium »

</details>