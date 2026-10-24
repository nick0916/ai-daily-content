---
id: inbox_9e3353a3
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0346-simon-willison-quick-study-3317]]"
title: "Quick Study"
url: https://simonwillison.net/2026/Oct/23/quick-study-painter/
source: simon-willison
published_at: 2026-10-23T21:35:13+00:00
fetched_at: 2026-10-24T03:51:18.238249+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 用一句 prompt 讓 Claude 做出一個幾秒內把照片「畫」成油畫風的網頁小工具。 **How** 使用 canvas 元素加上模擬畫筆，並以 Sobel 邊緣偵測決定筆觸，除 Google Fonts 外不依賴外部函式庫。 **What** 工具名為 Quick Study，prompt 給 Claude Opus 5.5 High：開啟照片後數秒內用模擬畫筆繪出該照片的版本。他也提到先前曾讓 Claude Fable 用 P5.js 模擬水彩插畫。"
key_points:
  - "Quick Study 由 Claude Opus 5.5 High 依單一 prompt 生成 artifact"
  - "技術為 canvas 元素加模擬畫筆，以 Sobel 邊緣偵測驅動，無外部函式庫（僅 Google Fonts）"
  - "延續先前用 Claude Fable 搭配 P5.js 模擬水彩插畫的實驗"
tags: [simon-willison, claude-opus, artifact, canvas, sobel-edge-detection]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Quick Study

Simon Willison 用一句 prompt 讓 Claude 做出一個幾秒內把照片「畫」成油畫風的網頁小工具。 **How** 使用 canvas 元素加上模擬畫筆，並以 Sobel 邊緣偵測決定筆觸，除 Google Fonts 外不依賴外部函式庫。 **What** 工具名為 Quick Study，prompt 給 Claude Opus 5.5 High：開啟照片後數秒內用模擬畫筆繪出該照片的版本。他也提到先前曾讓 Claude Fable 用 P5.js 模擬水彩插畫。

### 重點
- Quick Study 由 Claude Opus 5.5 High 依單一 prompt 生成 artifact
- 技術為 canvas 元素加模擬畫筆，以 Sobel 邊緣偵測驅動，無外部函式庫（僅 Google Fonts）
- 延續先前用 Claude Fable 搭配 P5.js 模擬水彩插畫的實驗

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/23/quick-study-painter/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: Quick Study 
 Prompt to Claude Opus 5.5 High : 
 
 Build an artifact where you open a photo and it rapidly (in a few seconds) paints a version of that photo using a canvas element and simulated paintbrush 
 
 See also my previous experiment getting Claude Fable to simulate a watercolor illustration with P5.js. 
 
 Quick Study uses Sobel edge detection , with no external libraries beyond Google Fonts. 
 
 
 Tags: tools

</details>