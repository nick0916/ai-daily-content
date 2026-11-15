---
id: inbox_e4cf1e1a
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0126-hackernews-show-hn-isometric-sf-a-pixel-art-map-of-cdcc]]"
title: "Show HN: Isometric SF – A pixel-art map of the SF Bay Area"
url: https://isometricsf.com/
source: hackernews
published_at: 2026-11-13T17:58:37+00:00
fetched_at: 2026-11-15T01:29:47.323451+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "先用貴的大模型找出畫風，再把風格蒸成便宜的小模型 LoRA 去大量生成，成本只剩約四分之一。 **Why** 作者要把 1300 平方英里的灣區 3D 圖磚轉成統一的像素風地圖，直接用 Nano Banana 2 全部生成約需 7k 美元。 **How** 先用 Nano Banana 2 訓練 Qwen-Image-Edit 2511 LoRA 來原型驗證風格與生成方法，最終地圖再用 Qwen 訓練 Klein 4B LoRA 重現該風格。 **What** Isometric SF 把 Google Photorealistic 3D Tiles 轉成可探索的像素地圖，涵蓋 Apple Park、Palace of Fine Arts、UC Berkeley 等地標。Klein 4B LoRA 的成本約為原方案的 1/4；創意來自 Isometric NYC。"
key_points:
  - "流程：Nano Banana 2 → 訓練 Qwen-Image-Edit 2511 LoRA 做風格原型 → Qwen 訓練 Klein 4B LoRA 產出最終地圖"
  - "Klein 4B LoRA 重現風格的成本為 1/4；若全用 Nano Banana 2 約需 7k 美元"
  - "來源為 Google Photorealistic 3D Tiles，涵蓋約 1300 平方英里灣區"
tags: [lora, fine-tuning, qwen-image-edit, nano-banana-2, image-generation]
topics: [foundation_models.open_weights, research.training]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Isometric SF – A pixel-art map of the SF Bay Area

先用貴的大模型找出畫風，再把風格蒸成便宜的小模型 LoRA 去大量生成，成本只剩約四分之一。

**Why** 作者要把 1300 平方英里的灣區 3D 圖磚轉成統一的像素風地圖，直接用 Nano Banana 2 全部生成約需 7k 美元。

**How** 先用 Nano Banana 2 訓練 Qwen-Image-Edit 2511 LoRA 來原型驗證風格與生成方法，最終地圖再用 Qwen 訓練 Klein 4B LoRA 重現該風格。

**What** Isometric SF 把 Google Photorealistic 3D Tiles 轉成可探索的像素地圖，涵蓋 Apple Park、Palace of Fine Arts、UC Berkeley 等地標。Klein 4B LoRA 的成本約為原方案的 1/4；創意來自 Isometric NYC。

### 重點
- 流程：Nano Banana 2 → 訓練 Qwen-Image-Edit 2511 LoRA 做風格原型 → Qwen 訓練 Klein 4B LoRA 產出最終地圖
- Klein 4B LoRA 重現風格的成本為 1/4；若全用 Nano Banana 2 約需 7k 美元
- 來源為 Google Photorealistic 3D Tiles，涵蓋約 1300 平方英里灣區

**原文：** [hackernews](https://isometricsf.com/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Technical Write-up: https://www.justinchavez.com/blog/isometric-sf-how/ Hi HN! Showcasing this fun project. I took 1300 square miles of the SF Bay Area from Google Photorealistic 3D Tiles and transformed them into a cohesive pixel map. It's really fun to explore and stumble upon various famous landmarks like Apple Park, Palace of Fine Arts, or UC Berkeley. The technicals involve using Nano Banana 2 to train a Qwen-Image-Edit 2511 LoRA which is used to prototype the style and generation methods. For final map I used Qwen to train a Klein 4B LoRA which reproduced the style at 1/4 of the cost. More details in the blog post. Let me know what you think! I really enjoyed this process of fine-tuning smaller open source models. If I did the map with Nano Banana 2 it would have cost around 7k USD! Credit for the idea goes to Isometric NYC.

</details>