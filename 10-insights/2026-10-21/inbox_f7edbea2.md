---
id: inbox_f7edbea2
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-infoq-main-article-distributed-spring-batch-without-c04d]]"
title: "Article: Distributed Spring Batch Without a Message Broker"
url: https://www.infoq.com/articles/spring-batch-without-broker/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-21T09:00:00+00:00
fetched_at: 2026-10-21T23:42:18.417426+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "分散式批次處理不用訊息佇列，直接用已有的資料庫來協調各節點。 **Why** Spring Batch 分散式 partitioning 本來就需要共享且持久的 job repository，再加 message broker 是額外的複雜度。 **How** 讓資料庫成為整個協調平面：依即時節點數切分工作、每個 job 有各自的 master 而無常駐協調者、用 compare-and-set 搶佔任務避免重複執行、以兩階段 heartbeat 做故障轉移。 **What** Janardhan Reddy Chejarla 的文章說明此無 broker 架構，也指出哪些情境仍適合使用 broker。"
key_points:
  - "以 compare-and-set claiming 防止任務重複執行"
  - "兩階段 heartbeat 故障轉移，無常駐協調者（per-job master）"
  - "依即時節點數調整工作切分，並說明 broker 仍適用的情境"
tags: [spring-batch, distributed-systems, database-coordination, failover, java]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Distributed Spring Batch Without a Message Broker

分散式批次處理不用訊息佇列，直接用已有的資料庫來協調各節點。

**Why** Spring Batch 分散式 partitioning 本來就需要共享且持久的 job repository，再加 message broker 是額外的複雜度。

**How** 讓資料庫成為整個協調平面：依即時節點數切分工作、每個 job 有各自的 master 而無常駐協調者、用 compare-and-set 搶佔任務避免重複執行、以兩階段 heartbeat 做故障轉移。

**What** Janardhan Reddy Chejarla 的文章說明此無 broker 架構，也指出哪些情境仍適合使用 broker。

### 重點
- 以 compare-and-set claiming 防止任務重複執行
- 兩階段 heartbeat 故障轉移，無常駐協調者（per-job master）
- 依即時節點數調整工作切分，並說明 broker 仍適用的情境

**原文：** [infoq-main](https://www.infoq.com/articles/spring-batch-without-broker/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Distributed Spring Batch partitioning already needs a shared, persistent job repository. This article makes that database the whole coordination plane and drops the message broker, sizing work to the live node count, a per-job master with no standing coordinator, compare-and-set claiming that prevents double-execution, two-phase heartbeat failover, and where a broker is still the right choice. By Janardhan Reddy Chejarla

</details>