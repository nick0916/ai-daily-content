---
id: inbox_de1dcad3
date: 2026-09-23
source_ref: "[[00-inbox/2026-09-23/0256-substack-vutrinh-free-one-clickhouse-query-took-down-20-o-4f91]]"
title: "[FREE] One ClickHouse Query Took Down 20% of the Internet for 5 Hours and 38 Minutes"
url: https://vutr.substack.com/p/free-one-clickhouse-query-took-down
source: substack-vutrinh
published_at: 2026-09-23T05:15:42+00:00
fetched_at: 2026-10-18T03:10:45.349790+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "這篇文章回顧 2025 年 11 月 18 日的 Cloudflare 當機事件。依標題，一個 ClickHouse 查詢造成約 20% 的網際網路受影響，持續 5 小時 38 分鐘。副標說明文章目的是拆解（demystify）這次事故。原文內容只有副標，沒有提供根因、受影響元件或修復過程等細節，因此無法確認查詢如何引發故障。這類事故分析對維運與基礎架構團隊有參考價值，但具體教訓需讀全文。"
key_points:
  - "事件日期：2025 年 11 月 18 日的 Cloudflare 當機"
  - "標題數字：影響約 20% 的網際網路、持續 5 小時 38 分鐘"
  - "標題指出肇因與一個 ClickHouse 查詢有關，根因細節輸入中未提供"
tags: [cloudflare, clickhouse, outage, postmortem]
topics: [engineering.architecture]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## [FREE] One ClickHouse Query Took Down 20% of the Internet for 5 Hours and 38 Minutes

這篇文章回顧 2025 年 11 月 18 日的 Cloudflare 當機事件。依標題，一個 ClickHouse 查詢造成約 20% 的網際網路受影響，持續 5 小時 38 分鐘。副標說明文章目的是拆解（demystify）這次事故。原文內容只有副標，沒有提供根因、受影響元件或修復過程等細節，因此無法確認查詢如何引發故障。這類事故分析對維運與基礎架構團隊有參考價值，但具體教訓需讀全文。

### 重點
- 事件日期：2025 年 11 月 18 日的 Cloudflare 當機
- 標題數字：影響約 20% 的網際網路、持續 5 小時 38 分鐘
- 標題指出肇因與一個 ClickHouse 查詢有關，根因細節輸入中未提供

**原文：** [substack-vutrinh](https://vutr.substack.com/p/free-one-clickhouse-query-took-down)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Demystifying the Cloudflare Outage on November 18, 2025

</details>