---
id: inbox_804a4c19
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2317-tomasz-tunguz-the-lakehouse-for-ai-872a]]"
title: "The Lakehouse for AI"
url: https://tomtunguz.com/the-lakehouse-for-ai/
source: tomasz-tunguz
published_at: 2026-11-17T00:00:00+00:00
fetched_at: 2026-11-17T23:25:44.357689+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "大型 AI 實驗室都用同一種資料湖格式（Lance）來存訓練與推論用的資料。 **Why** AI 研究要處理海量非結構化資料，傳統資料堆疊不夠用，LanceDB 的 Series B 標題即指 AI research outgrows the modern data stack。 **How** Lance 同時支援非結構化資料、欄位追加（column append）、分散式讀取與 ad-hoc SQL；Exa 靠欄位 backfill 只寫新資料、保留舊資料。 **What** 文中列出五個生產部署：Exa 在 Lance 存 35PB、涵蓋 100b 網頁，crawl 到搜尋延遲低於 5 分鐘；Adobe 管理 40–50PB、80 萬張表；Microsoft AI、Runway、NVIDIA Cosmos 也在用。LanceDB 募得 $57.5m Series B，Tomasz Tunguz 的 Theory 參與投資；自 Series A 起營收成長逾 10 倍，開源下載成長 6 倍、超過 1.2 億次。"
key_points:
  - "Exa：35PB Lance 資料表、100b 語意網頁、crawl 到搜尋延遲 < 5 分鐘；欄位 backfill 只寫新增資料"
  - "Adobe：40–50PB、800k 張表、每日 220b 事件，向上游貢獻 20+ PR；NVIDIA 在數千至數萬張 GPU 上直接以 Lance 資料表訓練"
  - "LanceDB $57.5m Series B；自 Series A 起營收成長 >10x、開源下載成長 6x 至 >120m"
tags: [lance, lancedb, lakehouse, ai-infrastructure, series-b]
topics: [engineering.architecture, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## The Lakehouse for AI

大型 AI 實驗室都用同一種資料湖格式（Lance）來存訓練與推論用的資料。

**Why** AI 研究要處理海量非結構化資料，傳統資料堆疊不夠用，LanceDB 的 Series B 標題即指 AI research outgrows the modern data stack。

**How** Lance 同時支援非結構化資料、欄位追加（column append）、分散式讀取與 ad-hoc SQL；Exa 靠欄位 backfill 只寫新資料、保留舊資料。

**What** 文中列出五個生產部署：Exa 在 Lance 存 35PB、涵蓋 100b 網頁，crawl 到搜尋延遲低於 5 分鐘；Adobe 管理 40–50PB、80 萬張表；Microsoft AI、Runway、NVIDIA Cosmos 也在用。LanceDB 募得 $57.5m Series B，Tomasz Tunguz 的 Theory 參與投資；自 Series A 起營收成長逾 10 倍，開源下載成長 6 倍、超過 1.2 億次。

### 重點
- Exa：35PB Lance 資料表、100b 語意網頁、crawl 到搜尋延遲 < 5 分鐘；欄位 backfill 只寫新增資料
- Adobe：40–50PB、800k 張表、每日 220b 事件，向上游貢獻 20+ PR；NVIDIA 在數千至數萬張 GPU 上直接以 Lance 資料表訓練
- LanceDB $57.5m Series B；自 Series A 起營收成長 >10x、開源下載成長 6x 至 >120m

**原文：** [tomasz-tunguz](https://tomtunguz.com/the-lakehouse-for-ai/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Read on tomtunguz.com → Across the largest AI labs & AI infrastructure companies, there is a common component : a lakehouse that stores data for training & inference called Lance. 
 Lance allows companies to manipulate massive collections of files in the most efficient way possible for AI. 
 

 Five production deployments show how that architecture runs at frontier scale : 
 Exa stores 35pb in Lance tables across 100b semantic web pages with crawl-to-search latency under five minutes. 1 Index lead Jan van der Vegt explained : 
 
 “These column backfills allow us to keep the old data in place & only write what is new.” 
 
 Runway runs Lance & LanceDB Enterprise across its video-generation stack. CTO Kamil Sindi noted : 2 
 
 “We first started using the Lance format in 2024 because it was the only option that handled unstructured data, column appends, distributed reads & ad-hoc SQL all at once.” 
 
 Microsoft AI runs LanceDB inside its own tenant & security boundary. Head of Data Platform Suqiang “Jack” Song shared : 3 
 
 “We rely on LanceDB as the data layer for training across billions of rows of image & code data, with distributed inference reading the format directly across thousands of nodes.” 
 
 Adobe manages 40pb to 50pb across 800k tables & 220b daily events, contributing 20+ pull requests upstream. 4 As Adobe’s platform team put it : 
 
 “Where should the AI-native data live? Our answer is in the same lakehouse, under the same contract as everything else.” 
 
 NVIDIA closed the loop on physical AI. Cosmos tech lead Max Li explained : 5 
 
 “First ever, we train on thousands & tens of thousands of GPUs at scale with Lance tables directly.” 
 
 Since its Series A last June, LanceDB has grown revenue more than 10x year over year across Netflix, Microsoft AI, Runway, Luma AI & Midjourney, while open-source downloads grew 6x past 120m. 6 
 Theory partnered with Chang She & Lei Xu at Seed & led their $30m Series A. 7 Today we are thrilled to join Bessemer Venture Partners & Innovation Endeavors, alongside Dimension, Swift Ventures, CRV & Y Combinator, in LanceDB’s $57.5m Series B. 
 Learn more about how to use Lance here . 
 
 
 
 
 Jan van der Vegt (Exa), Managing an Index of 100s of Billions of Pages with Exa Skeleton , Reverie Summit, November 5, 2026. ↩︎ 
 
 
 Ethan Rosenthal (Runway), Scalable, Multimodal Data Curation , Reverie Summit, November 5, 2026, & Kamil Sindi (CTO, Runway) in LanceDB’s Series B announcement. ↩︎ 
 
 
 Suqiang “Jack” Song (Head of Data Platform, Microsoft AI), Building the Data Flywheel for Frontier AI Model , Reverie Summit, November 5, 2026, & LanceDB Series B announcement. ↩︎ 
 
 
 Jing Chen He & Miao Wang (Adobe), How Adobe Built a Multimodal Lakehouse for AI-Native Experiences , Reverie Summit, November 5, 2026. ↩︎ 
 
 
 Max Li (Technical Lead, NVIDIA Cosmos), Cosmos : Omnimodal World Models for Physical AI , Reverie Summit, November 5, 2026, & LanceDB Series B announcement. ↩︎ 
 
 
 Chang She, “LanceDB Raises $57.5m as AI Research Outgrows the Modern Data Stack,” November 2026, & Yichen Wang (Luma AI), From Raw Delivery to the Training Loop : Luma’s Data Platform on Lance , Reverie Summit, November 5, 2026. ↩︎ 
 
 
 Tomasz Tunguz, A Data Foundation for Multimodal AI : Our Series A Investment in LanceDB , June 24, 2025. ↩︎

</details>