---
id: inbox_1eee813d
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0101-infoq-main-cloudflare-reclaims-100-tb-of-ram-by-opt-b1db]]"
title: "Cloudflare Reclaims 100 TB of RAM by Optimizing Consistent Hashing"
url: https://www.infoq.com/news/2026/10/cloudflare-hashing-optimization/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-24T08:10:00+00:00
fetched_at: 2026-10-25T01:09:02.668983+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把負載平衡服務裡的雜湊表壓得更緊，一次省下上百 TB 記憶體。 **Why** 內部負載平衡服務的 consistent hashing 記憶體佔用過大。 **How** 優化 pingora-ketama 的 Rust 實作，壓縮 hash ring 的條目，並用雜湊分佈與碰撞率的統計分析，把每個後端所需的雜湊數量減少約 90%。 **What** Cloudflare 公開紀錄，內部負載平衡服務的記憶體佔用減少超過 100 TB。"
key_points:
  - "對象為 Cloudflare 內部負載平衡服務所用的 Rust 函式庫 pingora-ketama"
  - "壓縮 hash ring 條目，並以雜湊分佈與碰撞率的統計分析決定所需雜湊數"
  - "每個後端的雜湊數量減少約 90%，整體記憶體佔用降低超過 100 TB"
tags: [cloudflare, consistent-hashing, pingora-ketama, rust, memory-optimization]
topics: [engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Reclaims 100 TB of RAM by Optimizing Consistent Hashing

把負載平衡服務裡的雜湊表壓得更緊，一次省下上百 TB 記憶體。

**Why** 內部負載平衡服務的 consistent hashing 記憶體佔用過大。

**How** 優化 pingora-ketama 的 Rust 實作，壓縮 hash ring 的條目，並用雜湊分佈與碰撞率的統計分析，把每個後端所需的雜湊數量減少約 90%。

**What** Cloudflare 公開紀錄，內部負載平衡服務的記憶體佔用減少超過 100 TB。

### 重點
- 對象為 Cloudflare 內部負載平衡服務所用的 Rust 函式庫 pingora-ketama
- 壓縮 hash ring 條目，並以雜湊分佈與碰撞率的統計分析決定所需雜湊數
- 每個後端的雜湊數量減少約 90%，整體記憶體佔用降低超過 100 TB

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/cloudflare-hashing-optimization/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare recently documented how it reduced the memory footprint of its internal load-balancing service by more than 100 TB by optimizing the Rust implementation of consistent hashing in pingora-ketama. The changes compacted hash-ring entries and used statistical analysis of hash distribution and collision rates to reduce the number of hashes per backend by about 90%. By Renato Losio

</details>