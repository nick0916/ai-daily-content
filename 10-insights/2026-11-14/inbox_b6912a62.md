---
id: inbox_b6912a62
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0124-infoq-main-google-cloud-moves-the-compute-engine-ap-ff63]]"
title: "Google Cloud Moves the Compute Engine API to Immutable Date-Based Versions"
url: https://www.infoq.com/news/2026/11/compute-engine-api-versioning/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-14T07:27:00+00:00
fetched_at: 2026-11-15T01:29:47.321103+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "API 不再只有一個會變動的版本，改成按日期凍結的快照，呼叫端自己選要用哪一版。 **Why** 單一可變的 /v1 介面一旦調整，所有呼叫端都會受影響。 **How** 以不可變的季度快照（如 2026-09-01）取代，每次請求透過 header 或 query parameter 指定版本。 **What** Google Cloud 的 Compute Engine API 正式（GA）採用日期式版本。新版本可更動預設值、錯誤格式與 IAM 檢查，而不影響 /v1 的呼叫端；Azure Resource Manager 與 Stripe 已用類似模式多年。"
key_points:
  - "Compute Engine API 以不可變季度快照（例：2026-09-01）取代單一可變的 /v1，已 GA"
  - "版本以 header 或 query parameter 逐請求選擇"
  - "新版本可改預設值、錯誤格式、IAM 檢查而不動到 /v1 呼叫端；Azure Resource Manager 與 Stripe 行之有年"
tags: [google-cloud, compute-engine, api-versioning, immutable-versions]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Google Cloud Moves the Compute Engine API to Immutable Date-Based Versions

API 不再只有一個會變動的版本，改成按日期凍結的快照，呼叫端自己選要用哪一版。

**Why** 單一可變的 /v1 介面一旦調整，所有呼叫端都會受影響。

**How** 以不可變的季度快照（如 2026-09-01）取代，每次請求透過 header 或 query parameter 指定版本。

**What** Google Cloud 的 Compute Engine API 正式（GA）採用日期式版本。新版本可更動預設值、錯誤格式與 IAM 檢查，而不影響 /v1 的呼叫端；Azure Resource Manager 與 Stripe 已用類似模式多年。

### 重點
- Compute Engine API 以不可變季度快照（例：2026-09-01）取代單一可變的 /v1，已 GA
- 版本以 header 或 query parameter 逐請求選擇
- 新版本可改預設值、錯誤格式、IAM 檢查而不動到 /v1 呼叫端；Azure Resource Manager 與 Stripe 行之有年

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/compute-engine-api-versioning/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google Cloud has made date-based versioning of the Compute Engine API generally available, replacing the single mutable /v1 surface with immutable quarterly snapshots such as 2026-09-01, selected per request with a header or query parameter. New versions can change defaults, error formats, and IAM checks without touching /v1 callers, a model Azure Resource Manager and Stripe have used for years. By Steef-Jan Wiggers

</details>