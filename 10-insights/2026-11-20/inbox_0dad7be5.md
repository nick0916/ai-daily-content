---
id: inbox_0dad7be5
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0237-simon-willison-llm-gemini-0-38-1-44b7]]"
title: "llm-gemini 0.38.1"
url: https://simonwillison.net/2026/Nov/20/llm-gemini/
source: simon-willison
published_at: 2026-11-20T03:01:57+00:00
fetched_at: 2026-11-22T02:43:02.036167+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 llm-gemini 外掛漏掉 Gemini 4 部分模型的最高推理等級。 **Why** Gemini 4 Carbon 只支援 low、medium、high，但 Hydrogen 與 Neon 多一個 xhigh，先前加入模型時遺漏。 **What** llm-gemini 0.38.1 補上 xhigh。Simon Willison 的比較顯示 Hydrogen 用 high 輸出 5,311 tokens、花費 3.99 美分，改用 xhigh 則輸出 31,477 tokens、花費 23.61 美分，產出的 pelican 圖能與 Gemini 4 Neon 競爭。"
key_points:
  - "Gemini 4 Hydrogen 與 Neon 支援 xhigh 推理等級，Carbon 僅有 low/medium/high"
  - "Hydrogen：high 為 5,311 output tokens、3.99 美分；xhigh 為 31,477 tokens、23.61 美分"
  - "llm-gemini 0.38.1 修正漏掉 xhigh 的問題"
tags: [llm-gemini, gemini-4, reasoning-levels, simon-willison, cost]
topics: [foundation_models.gemini]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-gemini 0.38.1

修正 llm-gemini 外掛漏掉 Gemini 4 部分模型的最高推理等級。

**Why** Gemini 4 Carbon 只支援 low、medium、high，但 Hydrogen 與 Neon 多一個 xhigh，先前加入模型時遺漏。

**What** llm-gemini 0.38.1 補上 xhigh。Simon Willison 的比較顯示 Hydrogen 用 high 輸出 5,311 tokens、花費 3.99 美分，改用 xhigh 則輸出 31,477 tokens、花費 23.61 美分，產出的 pelican 圖能與 Gemini 4 Neon 競爭。

### 重點
- Gemini 4 Hydrogen 與 Neon 支援 xhigh 推理等級，Carbon 僅有 low/medium/high
- Hydrogen：high 為 5,311 output tokens、3.99 美分；xhigh 為 31,477 tokens、23.61 美分
- llm-gemini 0.38.1 修正漏掉 xhigh 的問題

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/20/llm-gemini/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-gemini 0.38.1 
 Gemini 4 Carbon only supports low , medium and high reasoning levels - but Gemini 4 Hydrogen and Gemini 4 Neon both have an extra xhigh level. 
 I missed that when I added those models to the llm-gemini plugin, which is now fixed in this dot release. 
 The xhigh setting for Hydrogen makes a significant difference. I updated my Gemini 4 comparison grid - note how Hydrogen at high used 5,311 output tokens and cost 3.99 cents, but the same model at xhigh used 31,477 output tokens, cost 23.61 cents, and produced a pelican that's competitive with Gemini 4 Neon: 
 
 
 
 Tags: gemini , llm , llm-reasoning , pelican-riding-a-bicycle , ai , llms , google , generative-ai

</details>