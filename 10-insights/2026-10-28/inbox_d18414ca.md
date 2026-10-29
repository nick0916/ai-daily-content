---
id: inbox_d18414ca
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0017-infoq-main-cloudflare-opens-quicksilver-to-customer-fc5e]]"
title: "Cloudflare Opens Quicksilver to Customers as Workers KV Instant, Inside a 1 MB Envelope"
url: https://www.infoq.com/news/2026/10/workers-kv-instant/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-28T08:57:00+00:00
fetched_at: 2026-10-29T00:22:35.504639+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 把內部超快的鍵值儲存開放給客戶，讀取快很多，但容量限制很嚴。 **Why** 經典 Workers KV 讀取延遲偏高，部分場景需要更快的讀取。 **How** 把支撐 Cloudflare 幾乎所有請求的內部 key-value 儲存 Quicksilver，以 Workers KV 的一種模式開放。 **What** Quicksilver 以 Workers KV Instant 之名進入私有 beta；讀取 p99 為 1.62 ms，經典 KV 為 287 ms。限制為每個 namespace 10,000 個 key、1 MB、每秒一次寫入，決定了適用場景。"
key_points:
  - "Quicksilver 以 Workers KV 模式進入 private beta"
  - "讀取 p99 1.62 ms，對比經典 KV 的 287 ms"
  - "限制：每 namespace 10,000 keys、1 MB、每秒 1 次寫入"
tags: [cloudflare, workers-kv, quicksilver, key-value-store, edge]
topics: [engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Opens Quicksilver to Customers as Workers KV Instant, Inside a 1 MB Envelope

Cloudflare 把內部超快的鍵值儲存開放給客戶，讀取快很多，但容量限制很嚴。

**Why** 經典 Workers KV 讀取延遲偏高，部分場景需要更快的讀取。

**How** 把支撐 Cloudflare 幾乎所有請求的內部 key-value 儲存 Quicksilver，以 Workers KV 的一種模式開放。

**What** Quicksilver 以 Workers KV Instant 之名進入私有 beta；讀取 p99 為 1.62 ms，經典 KV 為 287 ms。限制為每個 namespace 10,000 個 key、1 MB、每秒一次寫入，決定了適用場景。

### 重點
- Quicksilver 以 Workers KV 模式進入 private beta
- 讀取 p99 1.62 ms，對比經典 KV 的 287 ms
- 限制：每 namespace 10,000 keys、1 MB、每秒 1 次寫入

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/workers-kv-instant/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare has put Quicksilver, the internal key-value store behind nearly every request it serves, into private beta as a Workers KV mode. Reads resolve in 1.62 ms at p99 against 287 ms for classic KV. The constraints decide the use case: 10,000 keys, one megabyte per namespace, and one write per namespace per second. By Steef-Jan Wiggers

</details>