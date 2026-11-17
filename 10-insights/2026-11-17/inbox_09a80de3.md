---
id: inbox_09a80de3
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2316-simon-willison-gpt6-2-astra-and-gpt6-2-sol-068c]]"
title: "GPT‐6.2 Astra and GPT‐6.2 Sol"
url: https://simonwillison.net/2026/Nov/17/gpt62-astra-and-sol/
source: simon-willison
published_at: 2026-11-17T22:38:52+00:00
fetched_at: 2026-11-17T23:21:49.083047+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 推出 GPT-6.2 兩個新模型：Astra 負責最難的任務，Sol 負責日常工作，且價格更便宜。 **Why** 長時間運行的 agent 工作階段成本高，降價（尤其是快取價格）對這類使用情境特別有利。 **What** API 名稱為 gpt-6.2-astra 與 gpt-6.2-sol。Astra 定價 $8/$40 每百萬 token（輸入/輸出），為 6 Astra（$10/$50）的 80%，快取價 $0.40 對比舊版 $1；Sol 維持 $2/$10。Simon Willison 已發布 LLM 0.38 支援這兩個模型；他的 Yonkers 機甲動畫測試中兩者表現都不如 Claude Fable 5.2 與 Gemini 4 Carbon。社群評價不一：Astra 6.2 在多項 benchmark 分數略低於 Fable 5.2，並有人反映其溝通風格令人困惑，Theo Browne 舉例指出它在長任務中會詢問使用者無法判斷的內部實作細節（/goal 任務兩小時後卡在詢問檔名）。"
key_points:
  - "gpt-6.2-astra 定價 $8/$40 per MTok（6 Astra 為 $10/$50），快取價 $0.40 vs 舊版 $1；與 Claude Fable 5.2 同價"
  - "gpt-6.2-sol 維持 $2/$10，約為 GPT-5.6 Sol（$4/$20）的一半"
  - "Astra 6.2 benchmark 略低於 Fable 5.2；Theo Browne 指出長任務中會問使用者無法判斷的內部實作細節"
tags: [gpt-6-2, llm-pricing, openai, llm-release, benchmark]
topics: [foundation_models.gpt]
importance: 5
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## GPT‐6.2 Astra and GPT‐6.2 Sol

OpenAI 推出 GPT-6.2 兩個新模型：Astra 負責最難的任務，Sol 負責日常工作，且價格更便宜。

**Why** 長時間運行的 agent 工作階段成本高，降價（尤其是快取價格）對這類使用情境特別有利。

**What** API 名稱為 gpt-6.2-astra 與 gpt-6.2-sol。Astra 定價 $8/$40 每百萬 token（輸入/輸出），為 6 Astra（$10/$50）的 80%，快取價 $0.40 對比舊版 $1；Sol 維持 $2/$10。Simon Willison 已發布 LLM 0.38 支援這兩個模型；他的 Yonkers 機甲動畫測試中兩者表現都不如 Claude Fable 5.2 與 Gemini 4 Carbon。社群評價不一：Astra 6.2 在多項 benchmark 分數略低於 Fable 5.2，並有人反映其溝通風格令人困惑，Theo Browne 舉例指出它在長任務中會詢問使用者無法判斷的內部實作細節（/goal 任務兩小時後卡在詢問檔名）。

### 重點
- gpt-6.2-astra 定價 $8/$40 per MTok（6 Astra 為 $10/$50），快取價 $0.40 vs 舊版 $1；與 Claude Fable 5.2 同價
- gpt-6.2-sol 維持 $2/$10，約為 GPT-5.6 Sol（$4/$20）的一半
- Astra 6.2 benchmark 略低於 Fable 5.2；Theo Browne 指出長任務中會問使用者無法判斷的內部實作細節

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/17/gpt62-astra-and-sol/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GPT‐6.2 Astra and GPT‐6.2 Sol 
OpenAI: 
 
 We’re introducing GPT‐6.2 Astra, our new frontier model for your hardest projects, and GPT‐6.2 Sol, our efficient, versatile model for everyday work. 
 
 They're available in the API as gpt-6.2-astra and gpt-6.2-sol . I shipped LLM 0.38 with support for the new models. 
 6.2 Astra is 80% of the price of 6 Astra - $8/MTok input and $40/MTok output, the same price as Claude Fable 5.2 (which was also 80% of its predecessor). 6 Astra and Fable 5 were both $10/$50. The cached price is an even bigger discount - $0.40/million compared to $1/million for the older model. This is great news for longer running agentic sessions. 
 GPT-6.2 Sol is the same $2/$10 price as 6.1 Sol and 6 Sol - which are half the price of GPT-5.6 Sol ($4/$20). 
 Here are the pelicans for GPT-6.2 Sol and for GPT-6.2 Astra . The 6.2 Astra max pelican looks like this: 
 
 I have a full comparison grid here , but here's how the high/xhigh/max pelicans compare with the previous Sol and Astra releases: 
 
 I also ran my most recent benchmark prompt against the two models, using "Ultra' effort levels in the Codex CLI: 
 
 Make a three js animation where yonkers stands up as a big mech (cool stand up motion) and stomps around manhattan and queens and Brooklyn, use openstreetmap mapping data 
 
 Here's Sol and here's Astra . Neither of them did a good enough job of morphing Yonkers into a big mech, at least in comparison to Claude Fable 5.2 and Gemini 4 Carbon . 
 This video showing the Astra and Sol animations playing out at the same time: 
 
 
 

 I created that video using GPT-6.2 Astra (Ultra) in the Codex desktop app by prompting: 
 
 https://static.simonwillison.net/static/2026/yonkers-gpt-6.2-astra-ultra/index.html and https://static.simonwillison.net/static/2026/yonkers-gpt-6.2-sol-ultra/index.html are two videos of the same thing by two different models 
 I need a video of the first 10 seconds where the top half of the video plays the first and the bottom half plays the second 
 I need an overlaid label of "GPT-6.2 Astra" on the top half and "GPT-6.2 Sol" on the bottom half. These labels should be tastefully positioned. 
 Make the video square and 2000x2000 pixels 
 
 Then later: 
 
 OK make it 20s 
 
 Here's the exported transcript . 
 The buzz around these new models is mixed at the moment. Astra 6.2 isn't scoring quite as high as Fable 5.2 on various benchmarks, and I've seen a few complaints that its communication style can be confusing. Theo Browne's review (in the form of a feedback letter he sent OpenAI during pre-release) has this useful example: 
 
 When this model is working on long tasks, it can pull in a lot of subagents and manage them pretty well. It will then proceed to randomly ask you some weird internal implementation detail bullshit that you could not under any earthly circumstance understand, much less have input on . 
 I sent "/goal make a new level for Outer Wilds". 2 hours in, it's "blocked" because it wanted to ask me "does r24's reviewer write it's clips to 24_g521.mp4 or 24_p11.mp4?" 
 

 Tags: ai , openai , generative-ai , llms , llm-pricing , pelican-riding-a-bicycle , llm-release , theo-browne , gpt , yonkers-rising

</details>