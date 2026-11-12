---
id: inbox_9ddea631
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-infoq-main-presentation-uncorking-queueing-bottlene-bccf]]"
title: "Presentation: Uncorking Queueing Bottlenecks with OpenTelemetry"
url: https://www.infoq.com/presentations/opentelemetry-queue-observability/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-11T11:00:00+00:00
fetched_at: 2026-11-12T02:59:23.372912+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 OpenTelemetry 追蹤取代對非同步佇列瓶頸的猜測。 **Why** 傳統指標無法說明分散式非同步佇列為何變慢，除錯只能靠猜。 **How** 以 OpenTelemetry tracing 觀察佇列，並依延遲分布訂定以使用者為中心的 SLO。 **What** Gearset 的 Oli Lane 與 Julian Wreford 在演講中分享實作方式與除錯技巧，對象為資深開發者、架構師與工程主管。"
key_points:
  - "Gearset 用 OpenTelemetry tracing 取代對非同步佇列的猜測"
  - "傳統指標不足，改用基於延遲分布的使用者導向 SLO"
  - "演講附實用除錯技巧"
tags: [opentelemetry, observability, queueing, slo, tracing]
topics: [engineering.architecture]
importance: 1
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Uncorking Queueing Bottlenecks with OpenTelemetry

用 OpenTelemetry 追蹤取代對非同步佇列瓶頸的猜測。

**Why** 傳統指標無法說明分散式非同步佇列為何變慢，除錯只能靠猜。

**How** 以 OpenTelemetry tracing 觀察佇列，並依延遲分布訂定以使用者為中心的 SLO。

**What** Gearset 的 Oli Lane 與 Julian Wreford 在演講中分享實作方式與除錯技巧，對象為資深開發者、架構師與工程主管。

### 重點
- Gearset 用 OpenTelemetry tracing 取代對非同步佇列的猜測
- 傳統指標不足，改用基於延遲分布的使用者導向 SLO
- 演講附實用除錯技巧

**原文：** [infoq-main](https://www.infoq.com/presentations/opentelemetry-queue-observability/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Oli Lane and Julian Wreford share how Gearset replaced guesswork in distributed asynchronous queues with OpenTelemetry tracing. They explain why traditional metrics fall short, how to implement user-centric SLOs based on latency distributions, and share practical debugging tips to help senior developers, software architects, and engineering leaders improve system reliability and team culture. By Julian Wreford, Oli Lane

</details>