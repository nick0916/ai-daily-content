---
id: inbox_8d747a1c
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-simon-willison-browse-tools-simonwillison-net-by-tag-182f]]"
title: "Browse tools.simonwillison.net by tag"
url: https://simonwillison.net/2026/Nov/11/tools-tags/
source: simon-willison
published_at: 2026-11-11T18:42:50+00:00
fetched_at: 2026-11-12T02:58:27.300321+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用程式碼靜態分析自動幫工具貼標籤，讓大量小工具更好瀏覽。 **Why** Simon 的 vibe-coded 工具已累積 244 個，缺乏好的瀏覽方式。 **How** 他讓模型用 tree-sitter 分析每個工具的程式碼，找出使用的 JavaScript API、函式庫與 web API 主機。 **What** tools.simonwillison.net 首頁新增依這些類別分組的 tag cloud（例如 Clipboard API 69、Canvas 2D 44、ES modules 92）；這項工作使用了他週重置前剩下的 Fable 5.2 額度。"
key_points:
  - "tools.simonwillison.net 目前有 244 個 vibe-coded 工具"
  - "以 tree-sitter 分析程式碼，抽取 JavaScript API、函式庫與 web API 主機作為標籤"
  - "首頁 tag cloud 範例：ES modules 92、Clipboard API 69、Canvas 2D 44"
tags: [tree-sitter, vibe-coding, tag-cloud, javascript, simon-willison]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Browse tools.simonwillison.net by tag

用程式碼靜態分析自動幫工具貼標籤，讓大量小工具更好瀏覽。

**Why** Simon 的 vibe-coded 工具已累積 244 個，缺乏好的瀏覽方式。

**How** 他讓模型用 tree-sitter 分析每個工具的程式碼，找出使用的 JavaScript API、函式庫與 web API 主機。

**What** tools.simonwillison.net 首頁新增依這些類別分組的 tag cloud（例如 Clipboard API 69、Canvas 2D 44、ES modules 92）；這項工作使用了他週重置前剩下的 Fable 5.2 額度。

### 重點
- tools.simonwillison.net 目前有 244 個 vibe-coded 工具
- 以 tree-sitter 分析程式碼，抽取 JavaScript API、函式庫與 web API 主機作為標籤
- 首頁 tag cloud 範例：ES modules 92、Clipboard API 69、Canvas 2D 44

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/11/tools-tags/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Browse tools.simonwillison.net by tag 
I've been wanting a better way to browse my collection of vibe-coded tools (244 and counting) for a while. I had a few Fable 5.2 credits left over before my weekly reset so I set it to work using tree-sitter to analyze the code for JavaScript APIs, libraries, and web API hosts used by each tool. 
 The homepage now features tag clouds for browsing by each of those categories of tag: 
 5, AbortController 6, Blob URLs 38, BroadcastChannel 1, Built-in AI 1, Camera / microphone 9, Canvas 2D 44, Clipboard API 69, Compression Streams 3, createImageBitmap 2, crypto random values 4, DOMParser 8, Drag and drop 30, Dynamic import() 12, ES modules 92" src="https://static.simonwillison.net/static/2026/tools-tag-cloud.webp" /> 

 Tags: javascript , tools , ai , generative-ai , llms , claude , vibe-coding

</details>