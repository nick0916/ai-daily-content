---
id: inbox_1e6e7cc0
date: 2026-10-19
source_ref: "[[00-inbox/2026-10-19/0205-infoq-main-pinterest-uses-event-time-watermarks-to-c8e9]]"
title: "Pinterest Uses Event Time Watermarks to Finalize Petabyte Scale Data Partitions"
url: https://www.infoq.com/news/2026/10/pinterest-event-time-partition/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-19T14:37:00+00:00
fetched_at: 2026-10-20T02:09:23.015157+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用事件時間水位線判斷持續匯入的資料何時夠完整，才能放行下游處理。 **Why** 持續匯入 CDC 資料時，下游作業需要知道某個分區何時已足夠完整。 **How** 以 Apache Flink 追蹤事件時間，並利用 Apache Iceberg metadata 發布不會倒退的水位線。 **What** Pinterest 為其資料庫匯入框架導入以事件時間為基礎的分區定案（partition finalization）機制，應用於 PB 等級的資料分區。"
key_points:
  - "Flink 負責追蹤事件時間"
  - "Iceberg metadata 用來發布 non-regressing watermark"
  - "目標是讓下游判斷 CDC 資料何時足夠完整"
tags: [pinterest, apache-flink, apache-iceberg, cdc, watermark]
topics: [engineering.architecture]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Pinterest Uses Event Time Watermarks to Finalize Petabyte Scale Data Partitions

用事件時間水位線判斷持續匯入的資料何時夠完整，才能放行下游處理。

**Why** 持續匯入 CDC 資料時，下游作業需要知道某個分區何時已足夠完整。

**How** 以 Apache Flink 追蹤事件時間，並利用 Apache Iceberg metadata 發布不會倒退的水位線。

**What** Pinterest 為其資料庫匯入框架導入以事件時間為基礎的分區定案（partition finalization）機制，應用於 PB 等級的資料分區。

### 重點
- Flink 負責追蹤事件時間
- Iceberg metadata 用來發布 non-regressing watermark
- 目標是讓下游判斷 CDC 資料何時足夠完整

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/pinterest-event-time-partition/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Pinterest has introduced event time-based partition finalization for its database ingestion framework. The mechanism uses Apache Flink to track event time and Apache Iceberg metadata to publish a non-regressing watermark, helping downstream jobs determine when continuously ingested CDC data is sufficiently complete for processing. By Leela Kumili

</details>