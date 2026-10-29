---
id: inbox_d04094ad
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0017-infoq-main-airbnb-cuts-recommendation-staleness-fro-7194]]"
title: "Airbnb Cuts Recommendation Staleness from 2 Days to Seconds with Chronon"
url: https://www.infoq.com/news/2026/10/airbnb-chronon-recommendation/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-28T13:53:00+00:00
fetched_at: 2026-10-29T00:22:35.500469+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓推薦系統的使用者行為特徵在幾秒內就更新，而不是等兩天。 **Why** 序列式推薦的 embedding 若更新太慢，就反映不出使用者最新的行為，推薦品質受限。 **How** 在 Chronon 特徵平台加入 Push Mode 與 Near Real-Time Model Transform，讓 embedding 以近即時方式更新。 **What** Airbnb 擴充 Chronon，將 embedding 過時時間從近兩天降到不到一分鐘；離線 NDCG 提升 1.67%，線上測試未取消訂單數增加約 0.3%（原文為約三分之一個百分點）。"
key_points:
  - "Chronon 新增 Push Mode 與 Near Real-Time Model Transform，用於更新序列式推薦 embedding"
  - "embedding 過時時間由近 2 天降至 1 分鐘以內"
  - "離線 NDCG +1.67%；線上 A/B 未取消訂單約 +0.33%"
tags: [airbnb, chronon, feature-platform, recommendation-system, near-real-time]
topics: [engineering.architecture]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Airbnb Cuts Recommendation Staleness from 2 Days to Seconds with Chronon

讓推薦系統的使用者行為特徵在幾秒內就更新，而不是等兩天。

**Why** 序列式推薦的 embedding 若更新太慢，就反映不出使用者最新的行為，推薦品質受限。

**How** 在 Chronon 特徵平台加入 Push Mode 與 Near Real-Time Model Transform，讓 embedding 以近即時方式更新。

**What** Airbnb 擴充 Chronon，將 embedding 過時時間從近兩天降到不到一分鐘；離線 NDCG 提升 1.67%，線上測試未取消訂單數增加約 0.3%（原文為約三分之一個百分點）。

### 重點
- Chronon 新增 Push Mode 與 Near Real-Time Model Transform，用於更新序列式推薦 embedding
- embedding 過時時間由近 2 天降至 1 分鐘以內
- 離線 NDCG +1.67%；線上 A/B 未取消訂單約 +0.33%

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/airbnb-chronon-recommendation/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Airbnb extended its Chronon feature platform with Push Mode and Near Real-Time Model Transform to update sequence-based recommendation embeddings within seconds. The architecture reduced embedding staleness from nearly two days to under a minute and improved offline NDCG by 1.67%, while online testing increased uncancelled bookings by approximately one-third of a percent. By Leela Kumili

</details>