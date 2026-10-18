---
id: inbox_affb832b
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-simon-willison-inline-rendering-with-document-currentsc-5e6c]]"
title: "Inline rendering with document.currentScript"
url: https://simonwillison.net/2026/Oct/17/document-currentscript/
source: simon-willison
published_at: 2026-10-17T21:11:12+00:00
fetched_at: 2026-10-18T03:03:45.773262+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 轉述 Lean Rada 的一個小技巧：利用 document.currentScript 屬性，在頁面中放一個行內 <script>，載入時用 replaceWith 把自己替換成運算結果。範例是 `The year is <script>document.currentScript.replaceWith(new Date().getFullYear())</script>`，直接把當前年份渲染到文字中。若再定義捷徑函式 `$=(...n)=>document.currentScript.replaceWith(...n)`，就能寫成 `<script>$(new Date().getFullYear())</script>`，形成一個極小的模板語言。實務意義是：在靜態 HTML 中不需要框架或建置流程，就能做簡單的行內動態渲染，適合小型工具頁與單檔 HTML 實驗。"
key_points:
  - "document.currentScript.replaceWith(...) 可讓行內 script 在載入時取代自身為運算結果"
  - "捷徑函式 $=(...n)=>document.currentScript.replaceWith(...n) 構成極簡模板語法"
  - "範例：<script>$(new Date().getFullYear())</script> 直接輸出當前年份"
tags: [javascript, document-currentscript, inline-rendering, html, web-tricks]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Inline rendering with document.currentScript

Simon Willison 轉述 Lean Rada 的一個小技巧：利用 document.currentScript 屬性，在頁面中放一個行內 <script>，載入時用 replaceWith 把自己替換成運算結果。範例是 `The year is <script>document.currentScript.replaceWith(new Date().getFullYear())</script>`，直接把當前年份渲染到文字中。若再定義捷徑函式 `$=(...n)=>document.currentScript.replaceWith(...n)`，就能寫成 `<script>$(new Date().getFullYear())</script>`，形成一個極小的模板語言。實務意義是：在靜態 HTML 中不需要框架或建置流程，就能做簡單的行內動態渲染，適合小型工具頁與單檔 HTML 實驗。

### 重點
- document.currentScript.replaceWith(...) 可讓行內 script 在載入時取代自身為運算結果
- 捷徑函式 $=(...n)=>document.currentScript.replaceWith(...n) 構成極簡模板語法
- 範例：<script>$(new Date().getFullYear())</script> 直接輸出當前年份

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/17/document-currentscript/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Inline rendering with document.currentScript 
Lean Rada describes a neat trick that takes advantage of the document.currentScript property. You can use that to drop in a tiny inline &lt;script&gt; element that replaces itself when the page loads: 
 The year is &lt;script&gt;
document.currentScript.replaceWith(
 new Date().getFullYear())&lt;/script&gt;
 
 If you define a shortcut function like this: 
 $=(...n)=&gt;document.currentScript.replaceWith(...n)
 
 You get a tiny template language: 
 The year is &lt;script&gt;$(new Date().getFullYear())&lt;/script&gt;
 

 Tags: javascript

</details>