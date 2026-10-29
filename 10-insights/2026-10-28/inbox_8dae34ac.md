---
id: inbox_8dae34ac
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0017-infoq-main-presentation-wrangling-telemetry-at-scal-d6a1]]"
title: "Presentation: Wrangling Telemetry at Scale: A Guide to Self-Hosted Observability"
url: https://www.infoq.com/presentations/self-hosted-observability-stack-tradeoffs/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-28T11:00:00+00:00
fetched_at: 2026-10-29T00:22:35.502782+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "教你自己架設可觀測性（監控、日誌、追蹤）系統，不依賴 SaaS 廠商。 **Why** 想避免被 SaaS 廠商綁定，但自架要面對工程上的取捨。 **How** 用開源工具串起 metrics、結構化 logs 與分散式 traces 並做關聯。 **What** Colin Douch 的演講，介紹以 Prometheus、VictoriaMetrics、Jaeger 自架可觀測性堆疊的實戰策略與取捨。"
key_points:
  - "使用 Prometheus、VictoriaMetrics、Jaeger 等開源工具自架可觀測性"
  - "重點在關聯 metrics、結構化 logs 與 distributed traces"
  - "討論避免 SaaS vendor lock-in 的工程取捨"
tags: [observability, self-hosted, prometheus, victoriametrics, jaeger]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Wrangling Telemetry at Scale: A Guide to Self-Hosted Observability

教你自己架設可觀測性（監控、日誌、追蹤）系統，不依賴 SaaS 廠商。

**Why** 想避免被 SaaS 廠商綁定，但自架要面對工程上的取捨。

**How** 用開源工具串起 metrics、結構化 logs 與分散式 traces 並做關聯。

**What** Colin Douch 的演講，介紹以 Prometheus、VictoriaMetrics、Jaeger 自架可觀測性堆疊的實戰策略與取捨。

### 重點
- 使用 Prometheus、VictoriaMetrics、Jaeger 等開源工具自架可觀測性
- 重點在關聯 metrics、結構化 logs 與 distributed traces
- 討論避免 SaaS vendor lock-in 的工程取捨

**原文：** [infoq-main](https://www.infoq.com/presentations/self-hosted-observability-stack-tradeoffs/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Colin Douch shares battle-tested strategies for building and scaling self-hosted observability stacks. He explains how to effectively correlate metrics, structured logs, and distributed traces using open-source tooling like Prometheus, VictoriaMetrics, and Jaeger, while navigating the engineering trade-offs of avoiding SaaS vendor lock-in. By Colin Douch

</details>