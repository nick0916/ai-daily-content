---
id: inbox_432ade86
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-infoq-main-linkedin-cuts-daily-spark-shuffle-fetch-86c1]]"
title: "LinkedIn Cuts Daily Spark Shuffle Fetch Failures from 750 to 20 with Apache Celeborn"
url: https://www.infoq.com/news/2026/11/linkedin-celeborn-remote-shuffle/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-18T15:05:00+00:00
fetched_at: 2026-11-19T08:18:32.248390+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "LinkedIn 改用獨立的遠端 shuffle 服務，讓大數據運算中途搬資料時不再常常失敗。 **Why** Spark／Flink 大規模作業的 shuffle 容易 fetch 失敗，造成重跑、浪費算力與拖慢執行時間。 **How** 部署 Apache Celeborn 作為共用遠端 shuffle 平台，透過專用儲存、副本（replication）與資料平面優化來提高穩定性。 **What** 涵蓋 LinkedIn 大多數 Spark 與 Flink 工作負載；每日 shuffle fetch 失敗從約 750 次降到 20 次，運算成本降 10%，應用執行時間改善 14%，每個 task 的 shuffle 成本降近 90%。"
key_points:
  - "每日 shuffle fetch 失敗由約 750 次降至 20 次"
  - "運算成本降 10%、應用執行時間改善 14%"
  - "每個 task 的 shuffle 成本降近 90%，靠專用儲存、replication 與 data-plane 優化"
tags: [linkedin, apache-celeborn, spark, flink, remote-shuffle, data-infrastructure]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## LinkedIn Cuts Daily Spark Shuffle Fetch Failures from 750 to 20 with Apache Celeborn

LinkedIn 改用獨立的遠端 shuffle 服務，讓大數據運算中途搬資料時不再常常失敗。

**Why** Spark／Flink 大規模作業的 shuffle 容易 fetch 失敗，造成重跑、浪費算力與拖慢執行時間。

**How** 部署 Apache Celeborn 作為共用遠端 shuffle 平台，透過專用儲存、副本（replication）與資料平面優化來提高穩定性。

**What** 涵蓋 LinkedIn 大多數 Spark 與 Flink 工作負載；每日 shuffle fetch 失敗從約 750 次降到 20 次，運算成本降 10%，應用執行時間改善 14%，每個 task 的 shuffle 成本降近 90%。

### 重點
- 每日 shuffle fetch 失敗由約 750 次降至 20 次
- 運算成本降 10%、應用執行時間改善 14%
- 每個 task 的 shuffle 成本降近 90%，靠專用儲存、replication 與 data-plane 優化

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/linkedin-celeborn-remote-shuffle/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

LinkedIn deployed Apache Celeborn as a shared remote shuffle platform across most Spark and Flink workloads, reducing daily shuffle fetch failures from approximately 750 to 20. The deployment also lowered compute costs by 10%, improved application runtimes by 14%, and reduced shuffle costs per task by nearly 90% through dedicated storage, replication, and data-plane optimizations. By Leela Kumili

</details>