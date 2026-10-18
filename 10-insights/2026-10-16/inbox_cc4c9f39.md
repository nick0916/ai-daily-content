---
id: inbox_cc4c9f39
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0256-infoq-main-uber-automates-dependency-analysis-acros-0202]]"
title: "Uber Automates Dependency Analysis Across Its Service Mesh"
url: https://www.infoq.com/news/2026/10/uber-automated-dependency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-16T14:39:00+00:00
fetched_at: 2026-10-18T03:13:54.320355+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 開發了自動化的依賴分析系統，利用 RPC middleware 與 production metrics，將呼叫端（caller）與下游服務的失敗進行關聯。系統把依賴分類為 fail-close、fail-open 或 unknown。此方法針對的是抽樣式 distributed tracing 在 Uber 龐大 service mesh 中難以捕捉罕見失敗的限制。可延伸的原則是：不依賴抽樣 trace，而在 RPC 層用全量 metrics 推斷依賴行為，是處理罕見失敗的一種做法（此為推論）。對維運大型微服務架構的團隊，有助於判斷服務故障時的爆炸半徑。原文摘要未提供準確度或覆蓋率等數字。"
key_points:
  - "透過 RPC middleware 與 production metrics 關聯 caller 與下游失敗"
  - "將依賴分為 fail-close、fail-open、unknown 三類"
  - "補足抽樣 distributed tracing 對罕見失敗的盲區"
tags: [uber, service-mesh, dependency-analysis, reliability, rpc-middleware]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Automates Dependency Analysis Across Its Service Mesh

Uber 開發了自動化的依賴分析系統，利用 RPC middleware 與 production metrics，將呼叫端（caller）與下游服務的失敗進行關聯。系統把依賴分類為 fail-close、fail-open 或 unknown。此方法針對的是抽樣式 distributed tracing 在 Uber 龐大 service mesh 中難以捕捉罕見失敗的限制。可延伸的原則是：不依賴抽樣 trace，而在 RPC 層用全量 metrics 推斷依賴行為，是處理罕見失敗的一種做法（此為推論）。對維運大型微服務架構的團隊，有助於判斷服務故障時的爆炸半徑。原文摘要未提供準確度或覆蓋率等數字。

### 重點
- 透過 RPC middleware 與 production metrics 關聯 caller 與下游失敗
- 將依賴分為 fail-close、fail-open、unknown 三類
- 補足抽樣 distributed tracing 對罕見失敗的盲區

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/uber-automated-dependency/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber has developed an automated dependency analysis system that uses RPC middleware and production metrics to correlate caller and downstream failures. The approach classifies dependencies as fail-close, fail-open, or unknown and addresses limitations of sampled distributed tracing for rare failures across Uber’s large service mesh. By Leela Kumili

</details>