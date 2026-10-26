---
id: inbox_e733d69b
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-infoq-main-csiro-uses-serverless-architecture-to-qu-0830]]"
title: "CSIRO Uses Serverless Architecture to Query 100x More Genomic Variants on AWS"
url: https://www.infoq.com/news/2026/10/csiro-serverless-genomic-variant/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-23T14:30:00+00:00
fetched_at: 2026-10-24T03:51:37.200001+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "澳洲 CSIRO 不把基因變異檔案複製進中央資料庫，而是直接在雲端原檔上做查詢。 **Why** 基因體資料量龐大，把 VCF 檔複製進中央資料庫成本高、也難以擴展。 **How** 用 Amazon S3、Lambda、Athena、DynamoDB 組成 serverless 架構，以 metadata 索引搭配 HTTP byte range request，只讀取壓縮檔中需要的基因體區段。 **What** CSIRO 的 Serverless Beacon，可查詢比先前多 100 倍的基因變異；測試中 10,000 鹼基對查詢平均延遲 1.52 秒。"
key_points:
  - "架構組成：Amazon S3、Lambda、Athena、DynamoDB"
  - "以 metadata 索引 + HTTP byte range request 查詢壓縮基因體區域，免複製 VCF 進中央資料庫"
  - "測試結果：10,000 鹼基對查詢平均延遲 1.52 秒"
tags: [serverless, aws, genomics, csiro, byte-range-requests]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## CSIRO Uses Serverless Architecture to Query 100x More Genomic Variants on AWS

澳洲 CSIRO 不把基因變異檔案複製進中央資料庫，而是直接在雲端原檔上做查詢。

**Why** 基因體資料量龐大，把 VCF 檔複製進中央資料庫成本高、也難以擴展。

**How** 用 Amazon S3、Lambda、Athena、DynamoDB 組成 serverless 架構，以 metadata 索引搭配 HTTP byte range request，只讀取壓縮檔中需要的基因體區段。

**What** CSIRO 的 Serverless Beacon，可查詢比先前多 100 倍的基因變異；測試中 10,000 鹼基對查詢平均延遲 1.52 秒。

### 重點
- 架構組成：Amazon S3、Lambda、Athena、DynamoDB
- 以 metadata 索引 + HTTP byte range request 查詢壓縮基因體區域，免複製 VCF 進中央資料庫
- 測試結果：10,000 鹼基對查詢平均延遲 1.52 秒

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/csiro-serverless-genomic-variant/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

CSIRO has developed Serverless Beacon, a serverless architecture for querying genomic variants without copying VCF files into a central database. The system combines Amazon S3, Lambda, Athena and DynamoDB, using metadata indexes and HTTP byte range requests to query compressed genomic regions. Tests reported 1.52 second average latency for 10,000 base pair queries. By Leela Kumili

</details>