---
id: inbox_8bb695f1
date: 2026-10-13
source_ref: "[[00-inbox/2026-10-13/0256-infoq-architecture-presentation-how-eve-online-leverages-he-8c3f]]"
title: "Presentation: How Eve Online Leverages Head Based Sampling to Observe \&#34;Fun\&#34;"
url: https://www.infoq.com/presentations/eve-observability-head-sampling/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-10-13T11:00:00+00:00
fetched_at: 2026-10-18T03:15:28.761033+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "InfoQ 簡報中，Nicholas Herring 分享 EVE Online 如何在已運行 20 年的 MMO 架構上實作分散式追蹤（distributed tracing）與可觀測性。他討論的取樣技術包括 head-based sampling、動態指數移動平均（EMA）取樣，以及 deterministic sampling。目標是在高吞吐量的即時遊戲模擬下維持系統高保真度、控制 telemetry 成本，並避免效能退化。標題強調以此方式觀測「fun」。原文摘要未提供具體數字，細節需看簡報。對需要在高流量、低延遲系統中做 tracing 的工程團隊而言，可參考如何在成本與可見度之間取捨取樣策略。"
key_points:
  - "EVE Online 在 20 年歷史的 MMO 架構上導入分散式追蹤與可觀測性"
  - "組合使用 head-based、動態 EMA、deterministic 三種取樣技術"
  - "目標：維持高保真度、控制 telemetry 成本、避免高吞吐即時模擬下的效能退化"
tags: [observability, distributed-tracing, head-based-sampling, telemetry-cost, game-backend]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: How Eve Online Leverages Head Based Sampling to Observe \"Fun\"

InfoQ 簡報中，Nicholas Herring 分享 EVE Online 如何在已運行 20 年的 MMO 架構上實作分散式追蹤（distributed tracing）與可觀測性。他討論的取樣技術包括 head-based sampling、動態指數移動平均（EMA）取樣，以及 deterministic sampling。目標是在高吞吐量的即時遊戲模擬下維持系統高保真度、控制 telemetry 成本，並避免效能退化。標題強調以此方式觀測「fun」。原文摘要未提供具體數字，細節需看簡報。對需要在高流量、低延遲系統中做 tracing 的工程團隊而言，可參考如何在成本與可見度之間取捨取樣策略。

### 重點
- EVE Online 在 20 年歷史的 MMO 架構上導入分散式追蹤與可觀測性
- 組合使用 head-based、動態 EMA、deterministic 三種取樣技術
- 目標：維持高保真度、控制 telemetry 成本、避免高吞吐即時模擬下的效能退化

**原文：** [infoq-architecture](https://www.infoq.com/presentations/eve-observability-head-sampling/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Nicholas Herring shares how EVE Online tackles distributed tracing and observability across a 20-year-old MMO architecture. He discusses leveraging head-based, dynamic exponential moving average (EMA), and deterministic sampling techniques to maintain high system fidelity, control telemetry costs, and avoid performance degradation under high-throughput real-time game simulations. By Nicholas Herring

</details>