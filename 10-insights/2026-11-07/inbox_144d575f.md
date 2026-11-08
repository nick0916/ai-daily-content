---
id: inbox_144d575f
date: 2026-11-07
source_ref: "[[00-inbox/2026-11-07/0148-simon-willison-datasette-3046-don-t-serve-link-rel-next-72d3]]"
title: "datasette #3046: Don't serve link: rel=next HTTP headers to Firefox for HTML pages"
url: https://simonwillison.net/2026/Nov/7/link-rel-next/
source: simon-willison
published_at: 2026-11-07T23:57:46+00:00
fetched_at: 2026-11-08T01:53:36.748602+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 的分頁 HTTP header 會讓 Firefox 偷偷預先載入下一頁，造成無謂的伺服器負擔，作者因此停止對 Firefox 送出該 header。 **Why** 只有極少數訪客會點「下一頁」，但瀏覽器預取卻讓每次瀏覽都多抓資料，伺服器還得多渲染一整頁再丟掉。 **How** Datasette 頁面回傳 `link: ...; rel=\"next\"` header，Firefox 看到後會觸發 HTTP prefetch；解法是針對 Firefox 的 HTML 頁面不再送出這個 header。 **What** Datasette issue #3046。作者發現 Firefox 對此行為的相關 issue 已開了 24 年，其中有留言連到他自己 2002 年抱怨此功能的部落格文章，但他已完全忘記這個功能與當年的文章。"
key_points:
  - "Datasette 的 table 頁面送出 link rel=next HTTP header，導致 Firefox 自動預取下一頁資料"
  - "預取浪費瀏覽器流量，也讓 Datasette 伺服器白白渲染整頁；修法是不對 Firefox 的 HTML 頁面送此 header（issue #3046）"
  - "Firefox 針對此行為的 issue 已開放 24 年，作者 2002 年的部落格文章也曾提過"
tags: [datasette, firefox, http-prefetch, web-performance, simon-willison]
topics: [engineering.architecture]
importance: 1
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette #3046: Don't serve link: rel=next HTTP headers to Firefox for HTML pages

Datasette 的分頁 HTTP header 會讓 Firefox 偷偷預先載入下一頁，造成無謂的伺服器負擔，作者因此停止對 Firefox 送出該 header。

**Why** 只有極少數訪客會點「下一頁」，但瀏覽器預取卻讓每次瀏覽都多抓資料，伺服器還得多渲染一整頁再丟掉。

**How** Datasette 頁面回傳 `link: ...; rel="next"` header，Firefox 看到後會觸發 HTTP prefetch；解法是針對 Firefox 的 HTML 頁面不再送出這個 header。

**What** Datasette issue #3046。作者發現 Firefox 對此行為的相關 issue 已開了 24 年，其中有留言連到他自己 2002 年抱怨此功能的部落格文章，但他已完全忘記這個功能與當年的文章。

### 重點
- Datasette 的 table 頁面送出 link rel=next HTTP header，導致 Firefox 自動預取下一頁資料
- 預取浪費瀏覽器流量，也讓 Datasette 伺服器白白渲染整頁；修法是不對 Firefox 的 HTML 頁面送此 header（issue #3046）
- Firefox 針對此行為的 issue 已開放 24 年，作者 2002 年的部落格文章也曾提過

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/7/link-rel-next/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

datasette #3046: Don't serve link: rel=next HTTP headers to Firefox for HTML pages 
I was looking at the Firefox network panel today when I noticed that requests to a Datasette table page were triggering an HTTP prefetch to the next page of rows in that table. 
 This was happening because Datasette pages serve an HTTP link header like this: 
 link: ; rel="next" 
 This is bad. A tiny fraction of the visitors to one of those pages will click the "next" link, which means their browser is fetching unnecessary data and the Datasette server is having to render an entire page that then gets thrown away. 
 I dug in and learned that Firefox has an issue that has been open for 24 years about this behavior... 
 And one of the early comments on that issue links to my blog post from 2002 complaining about this feature. I hadn't just forgotten that I had written about it, I had forgotten the feature entirely!

 Tags: firefox , html , mozilla , datasette

</details>