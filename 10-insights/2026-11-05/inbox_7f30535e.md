---
id: inbox_7f30535e
date: 2026-11-05
source_ref: "[[00-inbox/2026-11-05/0002-substack-bytebytego-the-hidden-work-behind-every-database-re-9c1c]]"
title: "The Hidden Work Behind Every Database Request"
url: https://blog.bytebytego.com/p/the-hidden-work-behind-every-database
source: substack-bytebytego
published_at: 2026-11-05T16:31:07+00:00
fetched_at: 2026-11-06T00:08:59.644650+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "資料庫收到一個請求時，實際做的事遠比使用者要求的多，這篇用放大倍率來衡量這個落差。 **Why** 儲存系統除了處理請求，還要做額外工作（快速找資料、當機後復原、支援並行交易），這些工作都有成本。 **How** 比較邏輯工作與實體成本的差異，分成讀取放大、寫入放大、空間放大三個面向，再看 B-tree 與 LSM tree 的表現，以及索引、過濾器、壓縮、快取的作用。 **What** ByteByteGo 的文章（取得的內文為節錄，僅含開頭與大綱）。舉例：讀一筆小紀錄可能要抓取多個資料區塊；更新一個值可能觸發多次寫入；維持高可用可能需要遠大於資料集本身的空間。"
key_points:
  - "讀取放大、寫入放大、空間放大是量測邏輯工作與實體成本差距的三個面向"
  - "文章比較 B-tree 與 LSM tree 各自的放大表現，並討論索引與過濾器如何以空間換取較少的讀取"
  - "還涵蓋壓縮與快取如何改善放大，以及放大造成的影響（內文節錄，細節未呈現）"
tags: [database, read-amplification, write-amplification, lsm-tree, b-tree]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Hidden Work Behind Every Database Request

資料庫收到一個請求時，實際做的事遠比使用者要求的多，這篇用放大倍率來衡量這個落差。

**Why** 儲存系統除了處理請求，還要做額外工作（快速找資料、當機後復原、支援並行交易），這些工作都有成本。

**How** 比較邏輯工作與實體成本的差異，分成讀取放大、寫入放大、空間放大三個面向，再看 B-tree 與 LSM tree 的表現，以及索引、過濾器、壓縮、快取的作用。

**What** ByteByteGo 的文章（取得的內文為節錄，僅含開頭與大綱）。舉例：讀一筆小紀錄可能要抓取多個資料區塊；更新一個值可能觸發多次寫入；維持高可用可能需要遠大於資料集本身的空間。

### 重點
- 讀取放大、寫入放大、空間放大是量測邏輯工作與實體成本差距的三個面向
- 文章比較 B-tree 與 LSM tree 各自的放大表現，並討論索引與過濾器如何以空間換取較少的讀取
- 還涵蓋壓縮與快取如何改善放大，以及放大造成的影響（內文節錄，細節未呈現）

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/the-hidden-work-behind-every-database)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Mostly, an application’s storage system has to do work only when users make requests to that application. However, there’s a difference between the work requested and the work that the storage system has to perform. A storage system does extra work as well, which is equally important. It can help you find data quickly, recover data after a crash, or support concurrent transactions. But this extra work also has a cost. For example, the request might involve reading a small record, but it can require fetching many blocks of data. Or when the user requests an update to some value, it can trigger multiple writes in the storage system. Also, if you want to keep the dataset highly available, it might require much more space than the actual size of the dataset. Read amplification, write amplification, and space amplification show the differences between logical work and physical cost. In this article, we’re going to look at these differences in detail. Here’s what we will cover: What is logical work and physical work in a database Read amplification Write amplification Space amplification The amplifications with B-trees The amplifications with LSM trees How indexes and filters use space to avoid reads How compression helps improve amplifications The role of caching The impact of amplification Logical Work and Physical Work 
 
 
 Read more

</details>