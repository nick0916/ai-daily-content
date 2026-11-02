---
id: inbox_d908ef1f
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2328-hackernews-show-hn-wikihack-hackertube-but-for-wiki-7d88]]"
title: "Show HN: Wikihack – HackerTube, but for Wikipedia articles mentioned on HN"
url: https://wikihack.netlify.app
source: hackernews
published_at: 2026-11-02T05:06:30+00:00
fetched_at: 2026-11-02T23:32:16.672001+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 Hacker News 上被提到的維基百科條目整理成可滑動瀏覽的資訊流。 **Why** 作者看了 Karpathy 的 Hackertube 和 Hackerbooks 後，想做同類型的 Wikipedia 版本，讓內容更容易瀏覽與互動。 **How** 爬取 HN 上所有提及維基百科的紀錄並排序，整個網站只靠前端提供。 **What** Wikihack 提供三種排序：Top（被連結最多次）、Random（隨機但略偏向高頻條目）、Rising（偏重過去 12 個月），也能看到條目是在哪裡被投稿、在哪些留言被提到。"
key_points:
  - "爬取 HN 上所有提及維基百科的紀錄並排序成資訊流"
  - "三種排序：Top（連結次數）、Random（略偏高頻）、Rising（偏重近 12 個月）"
  - "整站只用前端提供，可看條目在投稿與留言中的出處"
tags: [hacker-news, wikipedia, show-hn, feed]
topics: [product_and_org.product]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Wikihack – HackerTube, but for Wikipedia articles mentioned on HN

把 Hacker News 上被提到的維基百科條目整理成可滑動瀏覽的資訊流。

**Why** 作者看了 Karpathy 的 Hackertube 和 Hackerbooks 後，想做同類型的 Wikipedia 版本，讓內容更容易瀏覽與互動。

**How** 爬取 HN 上所有提及維基百科的紀錄並排序，整個網站只靠前端提供。

**What** Wikihack 提供三種排序：Top（被連結最多次）、Random（隨機但略偏向高頻條目）、Rising（偏重過去 12 個月），也能看到條目是在哪裡被投稿、在哪些留言被提到。

### 重點
- 爬取 HN 上所有提及維基百科的紀錄並排序成資訊流
- 三種排序：Top（連結次數）、Random（略偏高頻）、Rising（偏重近 12 個月）
- 整站只用前端提供，可看條目在投稿與留言中的出處

**原文：** [hackernews](https://wikihack.netlify.app)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

After seeing Karpathy's Hackertube and Hackerbooks, I just had to make Wikihack. I scraped all mentions of wikipedia on hackernews and ranked them, and turn them into a scrollable feed to make it a bit more easy to digest / interact with. You can see where people submitted the articles and where people mentioned it in comments. The top shows the most frequently linked articles. Random is random but slightly weighted towards the more frequently linked articles (a little bit like Wikipedia actually). Rising is ranked towards the past 12 months. The entire site is served only through the frontend -- I'll add more features if people enjoy this!

</details>