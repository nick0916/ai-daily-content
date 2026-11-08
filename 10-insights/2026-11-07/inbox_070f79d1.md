---
id: inbox_070f79d1
date: 2026-11-07
source_ref: "[[00-inbox/2026-11-07/0149-infoq-main-open-source-pg-vectorsearch-brings-more-799e]]"
title: "Open Source pg_vectorsearch Brings More Scalable Vector Search to PostgreSQL"
url: https://www.infoq.com/news/2026/11/postgresql-vector-search/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-07T09:49:00+00:00
fetched_at: 2026-11-08T01:53:36.762910+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Tiger Data 推出開源 PostgreSQL 擴充套件，用分區加壓縮做向量搜尋，取代 pgvector 的圖狀索引。 **Why** 圖狀的 HNSW 索引需要較多記憶體與建索引時間。 **How** pg_vectorsearch 的 PRISM 索引改用資料分區與壓縮，而非 HNSW 的圖結構，以降低記憶體需求與索引建置時間。 **What** Tiger Data 發布 pg_vectorsearch，目前為 alpha 階段，為開源的 PostgreSQL 向量相似度搜尋擴充套件。原文未提供效能數字。"
key_points:
  - "Tiger Data 發布開源 pg_vectorsearch，目前為 alpha"
  - "PRISM 索引用資料分區與壓縮，取代 pgvector HNSW 的圖狀做法"
  - "宣稱可降低記憶體需求與索引建置時間（原文無具體數字）"
tags: [pg-vectorsearch, postgresql, vector-search, pgvector, tiger-data]
topics: [engineering.rag]
importance: 2
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Open Source pg_vectorsearch Brings More Scalable Vector Search to PostgreSQL

Tiger Data 推出開源 PostgreSQL 擴充套件，用分區加壓縮做向量搜尋，取代 pgvector 的圖狀索引。

**Why** 圖狀的 HNSW 索引需要較多記憶體與建索引時間。

**How** pg_vectorsearch 的 PRISM 索引改用資料分區與壓縮，而非 HNSW 的圖結構，以降低記憶體需求與索引建置時間。

**What** Tiger Data 發布 pg_vectorsearch，目前為 alpha 階段，為開源的 PostgreSQL 向量相似度搜尋擴充套件。原文未提供效能數字。

### 重點
- Tiger Data 發布開源 pg_vectorsearch，目前為 alpha
- PRISM 索引用資料分區與壓縮，取代 pgvector HNSW 的圖狀做法
- 宣稱可降低記憶體需求與索引建置時間（原文無具體數字）

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/postgresql-vector-search/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tiger Data has released pg_vectorsearch, an open source PostgreSQL extension for vector similarity search, currently in alpha. Its PRISM index uses data partitioning and compression instead of the graph-based approach used by pgvector’s HNSW index, reducing memory requirements and index build times. By Renato Losio

</details>