---
id: inbox_a2de8fa6
date: 2026-10-12
source_ref: "[[00-inbox/2026-10-12/0256-simon-willison-datasette-ports-0-4-032c]]"
title: "datasette-ports 0.4"
url: https://simonwillison.net/2026/Oct/12/datasette-ports/
source: simon-willison
published_at: 2026-10-12T04:57:07+00:00
fetched_at: 2026-10-18T03:05:17.816350+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發布 datasette-ports 0.4，這是他用來偵測並列出本機所有 Datasette 執行個體的外掛。新版已能配合最新版 Datasette 運作，並額外顯示偵測到的 PID。原文指出，知道 PID 之後，比較容易把新的 Python 3.15 profiler 掛接到對應的 Datasette 程序上。對象是在本機同時跑多個 Datasette 的使用者，以及想對 Datasette 做效能剖析的開發者。原文只是簡短的版本發布說明，沒有提供更多細節。"
key_points:
  - "datasette-ports 0.4 相容最新版 Datasette"
  - "新增顯示偵測到的 PID"
  - "PID 可方便掛接 Python 3.15 新 profiler"
tags: [datasette, datasette-ports, python-3-15, profiler, release]
topics: [engineering.inference]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-ports 0.4

Simon Willison 發布 datasette-ports 0.4，這是他用來偵測並列出本機所有 Datasette 執行個體的外掛。新版已能配合最新版 Datasette 運作，並額外顯示偵測到的 PID。原文指出，知道 PID 之後，比較容易把新的 Python 3.15 profiler 掛接到對應的 Datasette 程序上。對象是在本機同時跑多個 Datasette 的使用者，以及想對 Datasette 做效能剖析的開發者。原文只是簡短的版本發布說明，沒有提供更多細節。

### 重點
- datasette-ports 0.4 相容最新版 Datasette
- 新增顯示偵測到的 PID
- PID 可方便掛接 Python 3.15 新 profiler

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/12/datasette-ports/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-ports 0.4 
 My plugin for detecting and listing all Datasette instances on the current machine now works with the latest version, and displays the detected PID as well. Knowing the PID makes it easier to attach the new Python 3.15 profiler . 
 
 
 Tags: datasette

</details>