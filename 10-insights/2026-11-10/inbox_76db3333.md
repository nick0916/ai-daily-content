---
id: inbox_76db3333
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2322-simon-willison-llm-gemini-0-36-1d3d]]"
title: "llm-gemini 0.36"
url: https://simonwillison.net/2026/Nov/10/llm-gemini/
source: simon-willison
published_at: 2026-11-10T20:09:44+00:00
fetched_at: 2026-11-10T23:28:41.354988+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 最強的 Gemini 4 Carbon 從限定對象開放給所有人，並提供 llm-gemini 外掛支援。 **What** llm-gemini 0.36 支援 Gemini 4 Carbon，兩週前僅開放給部分網路防禦者，現在全面開放。上線價 $2/百萬輸入、$10/百萬輸出，12 月 1 日起翻倍為 $4/$20（與 Opus 5.5 同價）；支援 low/medium/high 思考強度，預設 medium。作者另以 Google Antigravity IDE 測試，Google 影片展示其 /swarm 功能協調子代理，做出 Three.js 的 3D 瀏覽器遊戲。"
key_points:
  - "Gemini 4 Carbon 定價 $2/$10，12/1 起調為 $4/$20"
  - "上線價與 GPT-6.1 Sol / Claude Sonnet 5.5 相同，漲價後與 Opus 5.5 相同"
  - "思考強度分 low/medium/high，預設 medium；Antigravity /swarm 可協調子代理"
tags: [gemini-4-carbon, llm-gemini, llm-pricing, antigravity, simon-willison]
topics: [foundation_models.gemini, agents.coding_agents]
importance: 4
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-gemini 0.36

Google 最強的 Gemini 4 Carbon 從限定對象開放給所有人，並提供 llm-gemini 外掛支援。

**What** llm-gemini 0.36 支援 Gemini 4 Carbon，兩週前僅開放給部分網路防禦者，現在全面開放。上線價 $2/百萬輸入、$10/百萬輸出，12 月 1 日起翻倍為 $4/$20（與 Opus 5.5 同價）；支援 low/medium/high 思考強度，預設 medium。作者另以 Google Antigravity IDE 測試，Google 影片展示其 /swarm 功能協調子代理，做出 Three.js 的 3D 瀏覽器遊戲。

### 重點
- Gemini 4 Carbon 定價 $2/$10，12/1 起調為 $4/$20
- 上線價與 GPT-6.1 Sol / Claude Sonnet 5.5 相同，漲價後與 Opus 5.5 相同
- 思考強度分 low/medium/high，預設 medium；Antigravity /swarm 可協調子代理

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/10/llm-gemini/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-gemini 0.36 
 Gemini 4 Carbon was announced two weeks ago for "a subset of cyber defenders", but today it's available to everyone else . 
 This is Google's best ever Gemini, priced at $2/million input and $10/million output at launch (that's GPT-6.1 Sol / Claude Sonnet 5.5 prices) but scheduled to double in price to $4/$20 on December 1st (same as Opus 5.5). 
 Here are three pelicans for the low, medium and high thinking efforts (it defaults to medium). This is the pelican I got for high: 
 
 Gemini pelicans have all been great for a while now, so I also tested it out using Google's Antigravity IDE with a prompt I first tried with Claude Fable 5.2 yesterday : 
 
 Make a three js animation where yonkers stands up as a big mech (cool stand up motion) and stomps around manhattan and queens and Brooklyn, use openstreetmap mapping data 
 
 Here's the HTML result (I had to prompt "build that into a standalone HTML file" to get a version with no external dependencies). I then screen-captured that as a video: 
 
 
 

 Update : Huh, just saw this on YouTube : 
 
 Using Google Antigravity’s /swarm feature, Carbon built an open-world 3D game where you explore Google’s Mountain View campus as a pelican riding a GBike — coordinating subagents to model 3D assets in Blender from Omni and Nano Banana references, build the browser game in Three.js with WebGL shaders, and pair procedural Web Audio sound effects with Lyria music. 
 
 
 
 
 Tags: llm-release , gemini , llm , google , generative-ai , ai , llms , pelican-riding-a-bicycle

</details>