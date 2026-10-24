---
id: inbox_e751b01e
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-medium-tag-llm-he-put-one-function-between-40-agents-an-94f5]]"
title: "He Put One Function Between 40 Agents and the Model That Reads Them. Cost Fell 86%."
url: https://medium.com/@hardik.goel214/he-put-one-function-between-40-agents-and-the-model-that-reads-them-cost-fell-86-001ac4376036?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-23T21:31:01+00:00
fetched_at: 2026-10-24T03:54:08.064065+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "在多個小模型 worker 與大模型之間加一層中介函式，據稱省下 86% 成本。 **Why** 作者發現 40 個 Claude Haiku worker 接到 Claude Sonnet 報告撰寫模型後，帳單落在錯誤的項目上。 **How** 在 agent 與讀取其輸出的模型之間加入一個 function。 **What** 標題宣稱成本下降 86%；原文片段未提供該 function 的實作細節。"
key_points:
  - "40 個 Claude Haiku worker 接到 Claude Sonnet 報告撰寫模型"
  - "帳單歸因落在錯誤的項目，促使作者重新調整架構"
  - "在 agent 與讀報告的模型之間加入一個 function，標題宣稱成本下降 86%"
tags: [multi-agent, cost-optimization, claude-haiku, claude-sonnet, agent-architecture]
topics: [agents.frameworks, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## He Put One Function Between 40 Agents and the Model That Reads Them. Cost Fell 86%.

在多個小模型 worker 與大模型之間加一層中介函式，據稱省下 86% 成本。 **Why** 作者發現 40 個 Claude Haiku worker 接到 Claude Sonnet 報告撰寫模型後，帳單落在錯誤的項目上。 **How** 在 agent 與讀取其輸出的模型之間加入一個 function。 **What** 標題宣稱成本下降 86%；原文片段未提供該 function 的實作細節。

### 重點
- 40 個 Claude Haiku worker 接到 Claude Sonnet 報告撰寫模型
- 帳單歸因落在錯誤的項目，促使作者重新調整架構
- 在 agent 與讀報告的模型之間加入一個 function，標題宣稱成本下降 86%

**原文：** [medium-tag-llm](https://medium.com/@hardik.goel214/he-put-one-function-between-40-agents-and-the-model-that-reads-them-cost-fell-86-001ac4376036?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A builder wired forty Claude Haiku workers into one Claude Sonnet report-writer, watched the bill land on the wrong line item, and fixed&#x2026; Continue reading on Medium »

</details>