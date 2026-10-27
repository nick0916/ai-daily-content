---
id: inbox_42df2637
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0124-simon-willison-webframe-evaluated-as-a-scraper-and-a-sa-73cb]]"
title: "webframe: evaluated as a scraper and a sandbox"
url: https://simonwillison.net/2026/Oct/26/webframe-evaluation/
source: simon-willison
published_at: 2026-10-26T16:15:00+00:00
fetched_at: 2026-10-27T01:31:24.033611+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓網頁像程式一樣在隱藏瀏覽器裡執行的小工具 webframe，被拿來評估能否當爬蟲與沙盒。 **Why** shot-scraper 依賴 Playwright，Simon Willison 想知道是否有更輕量的替代方案。 **How** webframe 以 Go 撰寫，建立在 glaze 函式庫上，借用系統瀏覽器（macOS 用 WKWebView、Linux 用 WebKitGTK、Windows 用 WebView2），不必內建瀏覽器引擎。它在隱藏的 headless web view 執行網頁，console.log() 輸出到 stdout，例外輸出到 stderr。 **What** webframe 由 Jeff Lindsay 開發，Simon 請 Claude Opus 5.5 試跑、做原型並產出研究報告，評估其作為沙盒與 shot-scraper JavaScript 式爬蟲的可行性。原文僅貼出 prompt，未列出評估結論。"
key_points:
  - "webframe：Go 寫成、基於 glaze，使用系統 WebView（WKWebView / WebKitGTK / WebView2）"
  - "行為：執行網頁，console.log 到 stdout、例外到 stderr，類似 shot-scraper javascript 但不依賴 Playwright"
  - "Simon 用 Claude Opus 5.5 當研究代理，評估沙盒與爬蟲用途"
tags: [webframe, scraping, sandbox, shot-scraper, headless-browser]
topics: [agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## webframe: evaluated as a scraper and a sandbox

讓網頁像程式一樣在隱藏瀏覽器裡執行的小工具 webframe，被拿來評估能否當爬蟲與沙盒。

**Why** shot-scraper 依賴 Playwright，Simon Willison 想知道是否有更輕量的替代方案。

**How** webframe 以 Go 撰寫，建立在 glaze 函式庫上，借用系統瀏覽器（macOS 用 WKWebView、Linux 用 WebKitGTK、Windows 用 WebView2），不必內建瀏覽器引擎。它在隱藏的 headless web view 執行網頁，console.log() 輸出到 stdout，例外輸出到 stderr。

**What** webframe 由 Jeff Lindsay 開發，Simon 請 Claude Opus 5.5 試跑、做原型並產出研究報告，評估其作為沙盒與 shot-scraper JavaScript 式爬蟲的可行性。原文僅貼出 prompt，未列出評估結論。

### 重點
- webframe：Go 寫成、基於 glaze，使用系統 WebView（WKWebView / WebKitGTK / WebView2）
- 行為：執行網頁，console.log 到 stdout、例外到 stderr，類似 shot-scraper javascript 但不依賴 Playwright
- Simon 用 Claude Opus 5.5 當研究代理，評估沙盒與爬蟲用途

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/26/webframe-evaluation/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Research: webframe: evaluated as a scraper and a sandbox 
 webframe is a neat little project from Jeff Lindsay which lets you "run a web page like a program" - you point it at a URL or file and it executes it in a hidden headless web view and outputs console.log() to standard output and any exceptions to standard error. 
 It's written in Go on top of the glaze library, which provides access to a system browser ("WKWebView on macOS, WebKitGTK on Linux, WebView2 on Windows") so it doesn't need to bundle its own browser engine. 
 It reminds me of my own shot-scraper javascript tool, albeit in a much smaller package that doesn't depend on Playwright. 
 I had Claude Opus 5.5 put it through its paces and prepare a research report for me. Here's the prompt I used: 
 
 Explore https://github.com/tractordev/webframe try running it and put it though its paces, build a few exploratory prototypes, then evaluate it as a potential sandboxing tool and as a tool for scraping web pages using the same patterns encouraged by the "shot-scraper JavaScript" command (see simonw/shot-scraper on GitHub, docs directory) 
 
 
 
 Tags: browsers , go , javascript , jeff-lindsay , shot-scraper

</details>