---
id: inbox_72b9ed41
date: 2026-11-15
source_ref: "[[00-inbox/2026-11-15/2316-simon-willison-datasette-apps-0-4a0-f645]]"
title: "datasette-apps 0.4a0"
url: https://simonwillison.net/2026/Nov/15/datasette-apps/
source: simon-willison
published_at: 2026-11-15T04:02:45+00:00
fetched_at: 2026-11-17T23:22:14.569682+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Datasette 內的沙箱小應用可以互相連結，組合成一套工具。 **Why** 單一小應用功能有限，應用之間需要能互相跳轉，才能分工，例如搜尋與詳情。 **How** 應用可讀取並使用網址中的 `#fragment`；支援的 URL scheme 會回報給 Datasette Agent，讓它在協助寫應用時能產生彼此連結的應用。 **What** datasette-apps 0.4a0：Datasette Apps 是在 Datasette 內執行的沙箱 HTML/JavaScript 應用（類似 Claude Artifacts，但能對你的資料執行 SQL）。新版支援連結，例如一個應用顯示單筆記錄細節，另一個獨立應用負責搜尋並連到前者。"
key_points:
  - "datasette-apps 0.4a0 新增連結支援：應用可透過網址 `#fragment` 接收參數"
  - "支援的 URL scheme 會回報給 Datasette Agent，使其能協助撰寫互相連結的應用"
  - "範例：搜尋應用連到另一個顯示單筆記錄細節的應用"
tags: [datasette-apps, datasette-agent, sandboxed-apps, url-fragments]
topics: [agents.frameworks]
importance: 2
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-apps 0.4a0

讓 Datasette 內的沙箱小應用可以互相連結，組合成一套工具。

**Why** 單一小應用功能有限，應用之間需要能互相跳轉，才能分工，例如搜尋與詳情。

**How** 應用可讀取並使用網址中的 `#fragment`；支援的 URL scheme 會回報給 Datasette Agent，讓它在協助寫應用時能產生彼此連結的應用。

**What** datasette-apps 0.4a0：Datasette Apps 是在 Datasette 內執行的沙箱 HTML/JavaScript 應用（類似 Claude Artifacts，但能對你的資料執行 SQL）。新版支援連結，例如一個應用顯示單筆記錄細節，另一個獨立應用負責搜尋並連到前者。

### 重點
- datasette-apps 0.4a0 新增連結支援：應用可透過網址 `#fragment` 接收參數
- 支援的 URL scheme 會回報給 Datasette Agent，使其能協助撰寫互相連結的應用
- 範例：搜尋應用連到另一個顯示單筆記錄細節的應用

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/15/datasette-apps/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-apps 0.4a0 
 Datasette Apps are sandboxed HTML and JavaScript applications that live inside Datasette - think Claude Artifacts, but these ones can run SQL queries against your data. 
 0.4a0 adds support for linking: you can link to an app with #fragments in the URL and the app can see and use those, plus supported URL schemes are reported back to Datasette Agent so it can help write apps that link to each other. 
 This means you can have e.g. an app that shows details about a specific record, and a completely separate app that searches those records and links to their representations in the first app. 
 
 
 Tags: datasette-agent , datasette-apps , datasette , urls

</details>