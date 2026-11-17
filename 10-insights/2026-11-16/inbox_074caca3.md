---
id: inbox_074caca3
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-infoq-main-airbnb-introduces-castle-for-training-na-d2f0]]"
title: "Airbnb Introduces CASTLE for Training Natural Language Search Models with Synthetic Data"
url: https://www.infoq.com/news/2026/11/airbnb-castle/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-16T12:25:00+00:00
fetched_at: 2026-11-17T23:24:44.535475+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Airbnb 用 AI 憑空生成搜尋問句與標註，解決新搜尋功能沒有真實流量可訓練的問題。 **Why** 自然語言搜尋剛上線時缺乏足夠的真實搜尋流量，模型無從訓練（冷啟動問題）。 **How** 以去識別化的訂房 session 為基礎，用 LLM 同時生成合成搜尋 query 與相關性標籤。 **What** Airbnb 研究團隊提出 CASTLE 框架，讓模型在真實搜尋流量累積前就能先行訓練。"
key_points:
  - "CASTLE 針對自然語言搜尋的冷啟動問題"
  - "資料來源為去識別化的訂房 session，由 LLM 聯合生成合成 query 與相關性標籤"
  - "可在真實搜尋流量足夠之前訓練搜尋模型"
tags: [airbnb, synthetic-data, search, cold-start, llm]
topics: [research.training, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Airbnb Introduces CASTLE for Training Natural Language Search Models with Synthetic Data

Airbnb 用 AI 憑空生成搜尋問句與標註，解決新搜尋功能沒有真實流量可訓練的問題。

**Why** 自然語言搜尋剛上線時缺乏足夠的真實搜尋流量，模型無從訓練（冷啟動問題）。

**How** 以去識別化的訂房 session 為基礎，用 LLM 同時生成合成搜尋 query 與相關性標籤。

**What** Airbnb 研究團隊提出 CASTLE 框架，讓模型在真實搜尋流量累積前就能先行訓練。

### 重點
- CASTLE 針對自然語言搜尋的冷啟動問題
- 資料來源為去識別化的訂房 session，由 LLM 聯合生成合成 query 與相關性標籤
- 可在真實搜尋流量足夠之前訓練搜尋模型

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/airbnb-castle/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Airbnb researchers have introduced CASTLE, a framework designed to address the cold-start problem in natural language search. The approach uses de-identified booking sessions and large language models (LLMs) to jointly generate synthetic search queries and relevance labels, enabling model training before sufficient real search traffic is available. By Robert Krzaczyński

</details>