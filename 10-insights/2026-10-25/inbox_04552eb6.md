---
id: inbox_04552eb6
date: 2026-10-25
source_ref: "[[00-inbox/2026-10-25/0124-simon-willison-seam-cutter-d868]]"
title: "Seam Cutter"
url: https://simonwillison.net/2026/Oct/25/seam-cutter/
source: simon-willison
published_at: 2026-10-25T15:10:19+00:00
fetched_at: 2026-10-27T01:31:24.034847+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 做了一個小工具，在圖片中間切一刀後滑動兩側，就能裁掉中間一段。 **Why** 他常用 iPhone 的 Tailor 把多張截圖拼成長圖，有時需要裁掉中間一段，例如遮掉對話紀錄中不相關的提示。 **What** Seam Cutter 可建立水平或垂直切線，讓兩側相對滑動，等同裁去圖片中間部分。這是個很小眾的單一用途工具。"
key_points:
  - "功能：在圖片上建立水平或垂直切線，滑動兩側以裁掉中間區段"
  - "使用情境：長截圖拼接後，遮蔽不相關內容（如對話中的 prompt）"
  - "搭配 iPhone 的 Tailor 拼圖流程"
tags: [seam-cutter, image-tool, simon-willison, screenshots]
topics: [product_and_org.product]
importance: 1
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Seam Cutter

Simon Willison 做了一個小工具，在圖片中間切一刀後滑動兩側，就能裁掉中間一段。

**Why** 他常用 iPhone 的 Tailor 把多張截圖拼成長圖，有時需要裁掉中間一段，例如遮掉對話紀錄中不相關的提示。

**What** Seam Cutter 可建立水平或垂直切線，讓兩側相對滑動，等同裁去圖片中間部分。這是個很小眾的單一用途工具。

### 重點
- 功能：在圖片上建立水平或垂直切線，滑動兩側以裁掉中間區段
- 使用情境：長截圖拼接後，遮蔽不相關內容（如對話中的 prompt）
- 搭配 iPhone 的 Tailor 拼圖流程

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/25/seam-cutter/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: Seam Cutter 
 I built this weird and very specific cropping tool - it lets you create a horizontal or vertical cut across an image, then slide the two sides relative to each other. Effectively it lets you crop out a section in the middle of an image. 
 I wanted this because I often use Tailor on my iPhone to stitch several screenshots together into lot long image, but sometimes I find myself wanting to crop out a section in the middle - to redact an irrelevant prompt from a transcript, for example. 
 
 
 Tags: tools

</details>