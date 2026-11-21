---
id: inbox_a68d40f4
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0047-infoq-main-uber-cuts-translation-cache-memory-by-up-e87b]]"
title: "Uber Cuts Translation Cache Memory by up to 90% While Keeping P99 Latency Below 1 MS"
url: https://www.infoq.com/news/2026/11/uber-go-translation-cache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-20T14:38:00+00:00
fetched_at: 2026-11-21T00:53:21.641455+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把翻譯快取的大部分資料從記憶體搬到磁碟，只留索引與熱門內容在記憶體，省下九成記憶體。 **Why** Go 語言的快取全放記憶體時，佔用大量 RAM 且垃圾回收（GC）負擔重。 **How** 採混合架構：keys 與高頻存取的 values 留在記憶體，其餘 values 放磁碟，減少 GC 壓力與記憶體用量。 **What** Uber 重新設計 Go 版翻譯快取，初始記憶體用量降低逾 90%，快取命中率維持在 99.9% 以上，磁碟快取 miss 的 p99 延遲低於 100 微秒。"
key_points:
  - "初始記憶體用量降低超過 90%"
  - "快取命中率維持 99.9% 以上"
  - "磁碟支援的 cache miss p99 延遲低於 100 微秒"
tags: [uber, go, cache, memory-optimization, garbage-collection]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Cuts Translation Cache Memory by up to 90% While Keeping P99 Latency Below 1 MS

把翻譯快取的大部分資料從記憶體搬到磁碟，只留索引與熱門內容在記憶體，省下九成記憶體。

**Why** Go 語言的快取全放記憶體時，佔用大量 RAM 且垃圾回收（GC）負擔重。

**How** 採混合架構：keys 與高頻存取的 values 留在記憶體，其餘 values 放磁碟，減少 GC 壓力與記憶體用量。

**What** Uber 重新設計 Go 版翻譯快取，初始記憶體用量降低逾 90%，快取命中率維持在 99.9% 以上，磁碟快取 miss 的 p99 延遲低於 100 微秒。

### 重點
- 初始記憶體用量降低超過 90%
- 快取命中率維持 99.9% 以上
- 磁碟支援的 cache miss p99 延遲低於 100 微秒

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/uber-go-translation-cache/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber redesigned its Go-based translation cache to reduce its initial memory footprint by more than 90% while maintaining a cache hit rate above 99.9% and p99 disk-backed cache miss latency below 100 microseconds. The hybrid architecture combines in-memory keys and frequently accessed values with disk-backed storage, reducing garbage-collection overhead and memory consumption. By Leela Kumili

</details>