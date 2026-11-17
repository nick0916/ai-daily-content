---
id: inbox_f62eb261
date: 2026-11-15
source_ref: "[[00-inbox/2026-11-15/2316-simon-willison-datasette-1-0a43-a725]]"
title: "datasette 1.0a43"
url: https://simonwillison.net/2026/Nov/15/datasette/
source: simon-willison
published_at: 2026-11-15T23:20:27+00:00
fetched_at: 2026-11-17T23:22:14.568398+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 1.0 系列推進到 1.0a43，新增串流輸出與頁面切換動畫，並修補安全問題。 **Why** 作者正大量借助 Claude Fable 5.2 來清掉 1.0 里程碑的項目，該里程碑目前完成 53%。 **How** 輸出 renderer 支援串流，外掛可透過新的 `Response.stream()` 一次串流表格所有資料列；頁面切換動畫則用 CSS `@view-transition { navigation: auto; }` 搭配 `view-transition-name`，並以 `prefers-reduced-motion: no-preference` 限定啟用。 **What** Datasette 1.0a43：內建 TSV/CSV 匯出改用串流；修補私有儲存查詢可能洩漏標題與 SQL（無法執行）的問題並發布 GitHub advisory；row 頁面 JSON 表示法定案、新增 copy-schema Web Component 與 `DatasetteModal.confirm()`。跨文件 view transition 目前支援 Safari 與 Chrome，作者預期 Firefox 162 於 2026 年 12 月 8 日支援。"
key_points:
  - "Datasette 1.0 里程碑完成 53%；1.0a43 新增 `Response.stream()`，內建 TSV/CSV 匯出改用串流輸出"
  - "安全修補：私有 stored query 可能暴露其標題與 SQL（不可執行），已發布 GitHub advisory"
  - "新增 CSS 跨頁 view transitions（`@view-transition { navigation: auto; }`），讓多頁應用導覽像 SPA；Safari/Chrome 已支援，Firefox 預計 162（2026/12/8）"
tags: [datasette, view-transitions, css, security-fix, streaming]
topics: [security, agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a43

Datasette 1.0 系列推進到 1.0a43，新增串流輸出與頁面切換動畫，並修補安全問題。

**Why** 作者正大量借助 Claude Fable 5.2 來清掉 1.0 里程碑的項目，該里程碑目前完成 53%。

**How** 輸出 renderer 支援串流，外掛可透過新的 `Response.stream()` 一次串流表格所有資料列；頁面切換動畫則用 CSS `@view-transition { navigation: auto; }` 搭配 `view-transition-name`，並以 `prefers-reduced-motion: no-preference` 限定啟用。

**What** Datasette 1.0a43：內建 TSV/CSV 匯出改用串流；修補私有儲存查詢可能洩漏標題與 SQL（無法執行）的問題並發布 GitHub advisory；row 頁面 JSON 表示法定案、新增 copy-schema Web Component 與 `DatasetteModal.confirm()`。跨文件 view transition 目前支援 Safari 與 Chrome，作者預期 Firefox 162 於 2026 年 12 月 8 日支援。

### 重點
- Datasette 1.0 里程碑完成 53%；1.0a43 新增 `Response.stream()`，內建 TSV/CSV 匯出改用串流輸出
- 安全修補：私有 stored query 可能暴露其標題與 SQL（不可執行），已發布 GitHub advisory
- 新增 CSS 跨頁 view transitions（`@view-transition { navigation: auto; }`），讓多頁應用導覽像 SPA；Safari/Chrome 已支援，Firefox 預計 162（2026/12/8）

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/15/datasette/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 1.0a43 
 I've been leaning hard into Claude Fable 5.2 to help knock things off the 1.0 milestone , which is now 53% complete. 
 The biggest 1.0 item in this release is streaming support for output renderers - the built-in TSV and CSV export mechanisms now use this as well, and plugins can register themselves as capable of streaming every row in a table in one go via the new Response.stream() method. 
 There are a couple of security fixes, one of which I deemed deserving of a GitHub advisory : private stored queries could be exposed, granting access to the title and SQL of the query (but not allowing that query to be executed). 
 There are dozens of smaller improvements. The row page JSON representation finally has a design suitable for 1.0 . A new Web Component provides copy-schema in various places. JSON in columns on the row page can be pretty-printed. There's a new DatasetteModal.confirm() JavaScript utility method. Plus dozens of bug fixes, including contributions by Zihan Dai , Peter Olkhovets , Ilya Khalafi , and Ankita Advitot . 
 The feature I'm most excited about is a pretty tiny one: I've added CSS multi-page view transitions to Datasette! Here's the commit - key CSS is as follows: 
 /* Enable cross-document view transitions, 
 for anyone without prefers-reduced-motion */ 
 @media ( prefers-reduced-motion : no-preference ) { 
 @view-transition { 
 navigation : auto ; 
 } 
 } 
 /* .facet-results should morph from old position to new */ 
 html : active-view-transition . content > . facet-results { 
 view-transition-name : facet-results ; 
 } 
 /* So should a .table-wrapper, provided it contains .rows-and-columns */ 
 html : active-view-transition . table-wrapper : has ( > table . rows-and-columns ) { 
 view-transition-name : rows-table ; 
 } 

 With that in place, navigations within Datasette - still staunchly a multi-page application - feel more like an SPA. This works on Safari and Chrome at the moment and I believe supports for Firefox is due to land in Firefox 162 on December 8th 2026 (seeing as they are no longer feature-flagged in Firefox Nightly.) 
 
 
 
 
 
 Tags: security , datasette , css , browsers , annotated-release-notes , firefox , javascript , safari , chrome

</details>