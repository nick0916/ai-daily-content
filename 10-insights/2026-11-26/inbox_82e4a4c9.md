---
id: inbox_82e4a4c9
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0054-hackernews-tell-hn-lots-of-ask-hns-again-0156]]"
title: "Tell HN: Lots of Ask HNs again"
url: https://news.ycombinator.com/item?id=50649864
source: hackernews
published_at: 2026-11-26T00:43:34+00:00
fetched_at: 2026-11-27T01:00:17.401630+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hacker News 修正 Ask HN 頁面內容枯竭的問題，改為獨立排序文字貼文。 **Why** /ask 頁面曾只顯示十幾篇貼文，原因是其資料池取自前 1500 名排序貼文，而無連結的文字貼文占比下降，導致該頁面被餓死。 **How** 另外計算一份獨立的 Ask HN 排序清單，不再依賴首頁的排序池。 **What** HN 管理者說明 Ask HN 即無 URL 的文字貼文，標題也可能是 Tell HN 或沒有前綴；修正後 /ask 又出現大量貼文。"
key_points:
  - "成因：/ask 資料池取自首頁用的前 1500 名排序清單，文字貼文占比下降而枯竭"
  - "解法：另外計算 Ask HN 專屬的排序清單"
  - "此為 HN 站務公告，與 AI 產業無直接關係"
tags: [hacker-news, site-meta]
topics: [product_and_org.product]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Tell HN: Lots of Ask HNs again

Hacker News 修正 Ask HN 頁面內容枯竭的問題，改為獨立排序文字貼文。

**Why** /ask 頁面曾只顯示十幾篇貼文，原因是其資料池取自前 1500 名排序貼文，而無連結的文字貼文占比下降，導致該頁面被餓死。

**How** 另外計算一份獨立的 Ask HN 排序清單，不再依賴首頁的排序池。

**What** HN 管理者說明 Ask HN 即無 URL 的文字貼文，標題也可能是 Tell HN 或沒有前綴；修正後 /ask 又出現大量貼文。

### 重點
- 成因：/ask 資料池取自首頁用的前 1500 名排序清單，文字貼文占比下降而枯竭
- 解法：另外計算 Ask HN 專屬的排序清單
- 此為 HN 站務公告，與 AI 產業無直接關係

**原文：** [hackernews](https://news.ycombinator.com/item?id=50649864)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

There have been questions about why the /ask page ( https://news.ycombinator.com/ask ) was running dry of Ask HNs - e.g.: Ask HN: Why is Ask HN only showing me 14 posts? - https://news.ycombinator.com/item?id=49984484 - Oct 2026 (47 comments) Ask HN: Why is pagination gone on "Ask HN", and showing only 19 items? - https://news.ycombinator.com/item?id=50280719 - Oct 2026 (3 comments) I believe I found the problem. The pool of stories for https://news.ycombinator.com/ask has traditionally been drawn from the ranked stories list from which we generate the frontpage. That list is restricted to the top 1500 ranked submissions, and it seems the % of submissions which are text posts (i.e. no linked URL) had declined enough to starve the Ask HN feed. The solution is to compute a separate list of ranked Ask HNs. p.s. "Ask HN" is the conventional name but it means text posts. The title can also start with "Tell HN" or nothing in particular. They're just posts which were submitted without a URL.

</details>