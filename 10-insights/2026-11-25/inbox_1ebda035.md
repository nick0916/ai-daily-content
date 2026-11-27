---
id: inbox_1ebda035
date: 2026-11-25
source_ref: "[[00-inbox/2026-11-25/0052-infoq-main-doordash-scales-dispatch-10x-while-maint-736f]]"
title: "DoorDash Scales Dispatch 10x While Maintaining 99.99% Peak Availability"
url: https://www.infoq.com/news/2026/11/doordash-dispatch-redesign/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-25T14:44:00+00:00
fetched_at: 2026-11-27T00:59:38.363891+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "DoorDash 把外送派單系統從一個大塊的最佳化引擎，拆成負責協調與負責運算的分散式架構。 **What** DoorDash 重新設計即時派單平台，以分散式架構取代單體最佳化引擎，將協調與運算分離。新系統吞吐量提升 10 倍，尖峰可用性超過 99.99%，並支援混合式機器學習推論與多代理強化學習，動態最佳化配送指派。"
key_points:
  - "單體最佳化引擎改為協調與運算分離的分散式架構"
  - "吞吐量提升 10 倍，尖峰可用性 >99.99%"
  - "支援混合式 ML 推論與 multi-agent reinforcement learning 動態最佳化配送指派"
tags: [doordash, distributed-systems, dispatch, reinforcement-learning, high-availability]
topics: [engineering.architecture, engineering.inference]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## DoorDash Scales Dispatch 10x While Maintaining 99.99% Peak Availability

DoorDash 把外送派單系統從一個大塊的最佳化引擎，拆成負責協調與負責運算的分散式架構。

**What** DoorDash 重新設計即時派單平台，以分散式架構取代單體最佳化引擎，將協調與運算分離。新系統吞吐量提升 10 倍，尖峰可用性超過 99.99%，並支援混合式機器學習推論與多代理強化學習，動態最佳化配送指派。

### 重點
- 單體最佳化引擎改為協調與運算分離的分散式架構
- 吞吐量提升 10 倍，尖峰可用性 >99.99%
- 支援混合式 ML 推論與 multi-agent reinforcement learning 動態最佳化配送指派

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/doordash-dispatch-redesign/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

DoorDash has redesigned its real-time dispatch platform, replacing a monolithic optimization engine with a distributed architecture that separates coordination from computation. The new system delivers 10x higher throughput and more than 99.99% peak availability. It also supports hybrid machine learning inference and multi-agent reinforcement learning to dynamically optimize delivery assignments. By Leela Kumili

</details>