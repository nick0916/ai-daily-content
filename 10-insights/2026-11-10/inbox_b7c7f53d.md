---
id: inbox_b7c7f53d
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2322-simon-willison-yonkers-rises-8e9c]]"
title: "Yonkers Rises"
url: https://simonwillison.net/2026/Nov/10/yonkers-rises/
source: simon-willison
published_at: 2026-11-10T03:53:04+00:00
fetched_at: 2026-11-10T23:28:41.356657+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 AI 把紐約約克斯鎮變成會站起來踩踏的巨型機甲動畫，順便測試 3D 建模能力。 **Why** 作者不知道 Yonkers 的位置，想透過動畫幫助記住它的位置與形狀，也想試 Claude Fable 5.2 的 3D 建模與動畫能力。 **How** 以 Fable 5.2 Medium 產生 Three.js 動畫，使用 OpenStreetMap 資料，讓 Yonkers 站起來踩過曼哈頓、皇后區與布魯克林。 **What** 作者的工具頁 Yonkers Rises；提示中的手機鍵盤錯字「átomos」被模型正確判斷為「stomps」。"
key_points:
  - "使用 Claude Fable 5.2 Medium 產生 Three.js 動畫"
  - "資料來源為 OpenStreetMap"
  - "模型正確推斷錯字「átomos」是「stomps」"
tags: [claude-fable-5-2, three-js, openstreetmap, simon-willison]
topics: [foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Yonkers Rises

用 AI 把紐約約克斯鎮變成會站起來踩踏的巨型機甲動畫，順便測試 3D 建模能力。

**Why** 作者不知道 Yonkers 的位置，想透過動畫幫助記住它的位置與形狀，也想試 Claude Fable 5.2 的 3D 建模與動畫能力。

**How** 以 Fable 5.2 Medium 產生 Three.js 動畫，使用 OpenStreetMap 資料，讓 Yonkers 站起來踩過曼哈頓、皇后區與布魯克林。

**What** 作者的工具頁 Yonkers Rises；提示中的手機鍵盤錯字「átomos」被模型正確判斷為「stomps」。

### 重點
- 使用 Claude Fable 5.2 Medium 產生 Three.js 動畫
- 資料來源為 OpenStreetMap
- 模型正確推斷錯字「átomos」是「stomps」

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/10/yonkers-rises/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: Yonkers Rises 
 I realized I didn't know where Yonkers was, so I looked it up on Google Maps and then, to help embed its location and shape in my head (and to try out Claude Fable 5.2's 3D modeling and animation skills), I prompted Fable 5.2 Medium to: 
 
 Make a three js animation where yonkers stands up as a big mech (cool stand up motion) and átomos around manhattan and queens and Brooklyn, use openstreetmap mapping data 
 
 It correctly deduced that "átomos" was a mobile keyboard typo for "stomps": 
 
 
 
 
 
 Tags: three-js , llms , ai , generative-ai , claude-mythos-fable

</details>