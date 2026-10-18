---
id: inbox_e727caee
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-simon-willison-latex-renderer-5d22]]"
title: "LaTeX renderer"
url: https://simonwillison.net/2026/Oct/15/latex/
source: simon-willison
published_at: 2026-10-15T02:07:28+00:00
fetched_at: 2026-10-18T03:04:25.945026+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 受 Paul Ford 與 Aboard Foundary 的新 web app Tiny Little Office 啟發，請 Claude Code（Opus 5.5 Extra）做了一個 LaTeX 渲染工具。Tiny Little Office 提供文書處理、大綱、簡報、試算表、計算機、繪圖、圖表、動畫、行事曆與行程規劃等編輯器，招牌做法是把整份文件資料存在 URL 的 #fragment，使每份文件都成為可收藏、可分享的連結。它還提供 llms.txt，教 agent 如何組出可渲染成文件的 URL。Simon 的 LaTeX 工具同樣以 fragment hash 載入程式碼，支援自訂壓縮字典的前綴，無 fragment 時顯示編輯器並可切換到渲染檢視。他後續再用幾句 prompt 要求比照既有 SVG in Markdown 工具，加入 iframe sandbox 以防 XSS，並加入從 URL 或 Gist 載入 LaTeX 的功能。工具使用 Pako 2.1.0、MathJax 4.1.3、faster-latex 0.3.1 與 DOMPurify 3.4.16。實務意義在於：把狀態放進 URL fragment 搭配 llms.txt，能讓 agent 直接產生可分享的文件連結。"
key_points:
  - "文件資料存於 URL #fragment，無需後端即可產生可收藏、可分享連結；搭配 llms.txt 告訴 agent 如何構造 URL"
  - "以 iframe sandbox 降低 XSS 風險，並沿用既有 SVG in Markdown 工具的 Gist/URL 載入機制"
  - "使用的函式庫版本：Pako 2.1.0、MathJax 4.1.3、faster-latex 0.3.1、DOMPurify 3.4.16"
tags: [latex, url-fragment, llms-txt, claude-code, sandbox]
topics: [agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## LaTeX renderer

Simon Willison 受 Paul Ford 與 Aboard Foundary 的新 web app Tiny Little Office 啟發，請 Claude Code（Opus 5.5 Extra）做了一個 LaTeX 渲染工具。Tiny Little Office 提供文書處理、大綱、簡報、試算表、計算機、繪圖、圖表、動畫、行事曆與行程規劃等編輯器，招牌做法是把整份文件資料存在 URL 的 #fragment，使每份文件都成為可收藏、可分享的連結。它還提供 llms.txt，教 agent 如何組出可渲染成文件的 URL。Simon 的 LaTeX 工具同樣以 fragment hash 載入程式碼，支援自訂壓縮字典的前綴，無 fragment 時顯示編輯器並可切換到渲染檢視。他後續再用幾句 prompt 要求比照既有 SVG in Markdown 工具，加入 iframe sandbox 以防 XSS，並加入從 URL 或 Gist 載入 LaTeX 的功能。工具使用 Pako 2.1.0、MathJax 4.1.3、faster-latex 0.3.1 與 DOMPurify 3.4.16。實務意義在於：把狀態放進 URL fragment 搭配 llms.txt，能讓 agent 直接產生可分享的文件連結。

### 重點
- 文件資料存於 URL #fragment，無需後端即可產生可收藏、可分享連結；搭配 llms.txt 告訴 agent 如何構造 URL
- 以 iframe sandbox 降低 XSS 風險，並沿用既有 SVG in Markdown 工具的 Gist/URL 載入機制
- 使用的函式庫版本：Pako 2.1.0、MathJax 4.1.3、faster-latex 0.3.1、DOMPurify 3.4.16

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/15/latex/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: LaTeX renderer 
 Inspired by Paul Ford and Aboard Foundary's new web app Tiny Little Office , which provides a suite of web app content editors (a Word Processor, Outliner, Presentation Builder, Spreadsheet, Calculator, Drawing Tool, Diagram Maker, Animator, Calendar, and Trip Planner). 
 Tiny Little Office's signature trick is to store all of the document data in the #fragment section of the URL, so every document created using it becomes a bookmarkable and shareable link. 
 It also has an llms.txt file telling agents how to construct URLs that will render as documents. Claude used that file to generate this link to a deck that explains how the URL format works: 
 
 Tiny Little Office inspired me to have Claude Code (Opus 5.5 Extra) build a similar tool that works with LaTeX. Here's the sequence of prompts I used: 
 
 I want a tool where you can link to it with a fragment hash #code-here and it treats that code as LaTeX and renders it really effectively. It should also support a prefix which means the latex is compressed with a custom compression dictionary optimized for latex. Use the best available latex render library from a CDN (consider WebAssembly too). If loaded without a fragment hash show an editor you can paste latex into and then toggle to a "rendered" view. That rendered view should be bookmarkable. The #fragment view should let you switch to edit source too. 
 
 Since it was working in my tools repo I told it to take inspiration from the &lt;iframe sandbox="..."&gt; mechanism used by my existing SVG in Markdown tool as protection against XSS risks: 
 
 Safe from XSS? We could run in an iframe sandbox like we do on the SVG markdown render project 
 
 I had it copy the Gist/URL loading feature from that tool as well: 
 
 We should have an option to load latex from a URL (or gist) similar to the markdown SVG tool 
 
 Here's an example link . The tool uses Pako 2.1.0 , MathJax 4.1.3 , faster-latex 0.3.1 , and DOMPurify 3.4.16 . 
 
 
 
 Tags: latex , paul-ford , tools , urls , ai , generative-ai , llms

</details>