---
id: inbox_d664302c
date: 2026-11-27
source_ref: "[[00-inbox/2026-11-27/0141-infoq-main-presentation-from-fan-out-to-fast-sub-10-0579]]"
title: "Presentation: From Fan-Out to Fast: Sub-100ms API Design in Distributed Systems"
url: https://www.infoq.com/presentations/sub-100ms-latency-distributed-systems/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-27T11:00:00+00:00
fetched_at: 2026-11-28T01:51:16.547795+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "教你把 API 回應壓到 100 毫秒內，關鍵是替每一跳分配延遲預算並消除尾端延遲。 **Why** 分散式系統中一個請求會扇出到多個服務，最慢的那一個會拖垮整體回應時間。 **How** 為每一跳設定延遲預算，權衡非同步 fan-out，調整 thread pool 大小，搭配快取與 circuit breaker 來避免尾端延遲瓶頸。 **What** Saranya Vedagiri 以 eBay 的實際規模經驗，在 InfoQ 簡報中講解低延遲分散式 API 設計與效能優先的工程實務。"
key_points:
  - "以 hop-by-hop latency budget 拆解整體 100ms 目標"
  - "涵蓋 async fan-out 取捨、thread pool 大小設定、快取、circuit breaker"
  - "目標是消除 tail-latency 瓶頸，建立 performance-first 工程習慣"
tags: [latency, distributed-systems, api-design, tail-latency, ebay]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: From Fan-Out to Fast: Sub-100ms API Design in Distributed Systems

教你把 API 回應壓到 100 毫秒內，關鍵是替每一跳分配延遲預算並消除尾端延遲。

**Why** 分散式系統中一個請求會扇出到多個服務，最慢的那一個會拖垮整體回應時間。

**How** 為每一跳設定延遲預算，權衡非同步 fan-out，調整 thread pool 大小，搭配快取與 circuit breaker 來避免尾端延遲瓶頸。

**What** Saranya Vedagiri 以 eBay 的實際規模經驗，在 InfoQ 簡報中講解低延遲分散式 API 設計與效能優先的工程實務。

### 重點
- 以 hop-by-hop latency budget 拆解整體 100ms 目標
- 涵蓋 async fan-out 取捨、thread pool 大小設定、快取、circuit breaker
- 目標是消除 tail-latency 瓶頸，建立 performance-first 工程習慣

**原文：** [infoq-main](https://www.infoq.com/presentations/sub-100ms-latency-distributed-systems/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Saranya Vedagiri explains how to design resilient, low-latency distributed APIs under 100ms. Drawing on practical scale at eBay, she discusses hop-by-hop latency budgets, async fanout tradeoffs, thread pool sizing, caching, and circuit breakers. Learn actionable strategies to eliminate tail-latency bottlenecks and establish performance-first engineering practices. By Saranya Vedagiri

</details>