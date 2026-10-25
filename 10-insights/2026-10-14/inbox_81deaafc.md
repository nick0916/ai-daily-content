---
id: inbox_81deaafc
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0102-lobsters-vibecoding-ito-build-terminal-ui-in-lua-59b5]]"
title: "ito - build terminal ui in lua"
url: https://uji.sh/ito
source: lobsters-vibecoding
published_at: 2026-10-14T17:27:10-05:00
fetched_at: 2026-10-25T01:29:34.905543+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 Lua 撰寫終端機 UI，並在編輯時即時預覽的互動式工作坊。 **How** 以 require 回傳建構 view 的函式，用 ito.state 管理會變動的值，以 VStack、HStack、Text 組合畫面，再用 :padding、:bold、:grow 等 modifier 鏈式調整排版與樣式。 **What** 網頁內可直接編輯範例，編輯出錯時會保留上一個可用的預覽；另提供 ito.md 指南，可交給 LLM 當作參考。"
key_points:
  - "以 require(\"ito\") 回傳建構 view 的函式，用 ito.state(value) 管理會變動的值"
  - "以 VStack、HStack、Text 組合 view，並以 :spacing(1)、:padding(2)、:grow()、:bold()、:dim() 調整排版與樣式"
  - "編輯時即時預覽；若編輯出錯，保留上一個可用預覽；另提供 ito.md 讓使用者交給 LLM 作為指南"
tags: [lua, terminal-ui, tui, live-preview, llm-friendly-docs]
topics: [product_and_org.product]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## ito - build terminal ui in lua

用 Lua 撰寫終端機 UI，並在編輯時即時預覽的互動式工作坊。 **How** 以 require 回傳建構 view 的函式，用 ito.state 管理會變動的值，以 VStack、HStack、Text 組合畫面，再用 :padding、:bold、:grow 等 modifier 鏈式調整排版與樣式。 **What** 網頁內可直接編輯範例，編輯出錯時會保留上一個可用的預覽；另提供 ito.md 指南，可交給 LLM 當作參考。

### 重點
- 以 require("ito") 回傳建構 view 的函式，用 ito.state(value) 管理會變動的值
- 以 VStack、HStack、Text 組合 view，並以 :spacing(1)、:padding(2)、:grow()、:bold()、:dim() 調整排版與樣式
- 編輯時即時預覽；若編輯出錯，保留上一個可用預覽；另提供 ito.md 讓使用者交給 LLM 作為指南

**原文：** [lobsters-vibecoding](https://uji.sh/ito)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Make something with Lua.

The same Lua

Views and modifiers

Try your changes

ITO / AN INTERACTIVE WORKSHOP

Build your own terminal UI.

Your earlier drafts are still available.

Start with require("ito") and return a function that builds a view. Use ito.state(value) for values that change.

Compose with VStack , HStack , Text , and the controls in ito.md .

Use :spacing(1) , :padding(2) , :grow() , :bold() , and :dim() to arrange and style your views.

Your preview updates as you edit. If an edit has an error, the last working preview stays visible.

Try Input flow for keyboard navigation, editing, and cancellation. Use the expand icon for fullscreen. Open ito.md for a guide you can give your LLM.

</details>