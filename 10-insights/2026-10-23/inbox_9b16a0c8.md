---
id: inbox_9b16a0c8
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0346-openai-blog-rapidly-scaling-online-storage-to-serve-8a77]]"
title: "Rapidly scaling online storage to serve over 1 billion ChatGPT users (Part II)"
url: https://openai.com/index/scaling-storage-one-billion-users-part-two
source: openai-blog
published_at: 2026-10-23T17:00:00+00:00
fetched_at: 2026-10-24T03:51:18.237305+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 說明如何擴充 ChatGPT 的線上儲存系統，讓超過 10 億用戶的資料讀取更快。 **Why** 用戶規模達 10 億以上時，儲存層需要可靠的多租戶隔離與低延遲讀取。 **How** 原文僅提到結合可靠的多租戶設計、全球快取與 Azure Cosmos DB。 **What** 這是 Habitat 儲存系統擴展系列的第二篇；OpenAI 表示 ChatGPT 的讀取速度提升 12 倍。內文僅有摘要，細節架構未提供。"
key_points:
  - "系統名稱為 Habitat，是 ChatGPT 的線上儲存層"
  - "採用可靠的多租戶、全球快取與 Azure Cosmos DB"
  - "官方宣稱讀取速度快 12 倍，服務對象超過 10 億 ChatGPT 用戶"
tags: [openai, chatgpt, storage, azure-cosmos-db, scaling]
topics: [engineering.architecture, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Rapidly scaling online storage to serve over 1 billion ChatGPT users (Part II)

OpenAI 說明如何擴充 ChatGPT 的線上儲存系統，讓超過 10 億用戶的資料讀取更快。 **Why** 用戶規模達 10 億以上時，儲存層需要可靠的多租戶隔離與低延遲讀取。 **How** 原文僅提到結合可靠的多租戶設計、全球快取與 Azure Cosmos DB。 **What** 這是 Habitat 儲存系統擴展系列的第二篇；OpenAI 表示 ChatGPT 的讀取速度提升 12 倍。內文僅有摘要，細節架構未提供。

### 重點
- 系統名稱為 Habitat，是 ChatGPT 的線上儲存層
- 採用可靠的多租戶、全球快取與 Azure Cosmos DB
- 官方宣稱讀取速度快 12 倍，服務對象超過 10 億 ChatGPT 用戶

**原文：** [openai-blog](https://openai.com/index/scaling-storage-one-billion-users-part-two)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Learn how OpenAI scaled Habitat with reliable multi-tenancy, global caching, and Azure Cosmos DB to deliver 12× faster reads for ChatGPT.

</details>