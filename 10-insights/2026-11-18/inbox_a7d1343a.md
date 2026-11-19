---
id: inbox_a7d1343a
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-simon-willison-llm-gemini-0-38-2830]]"
title: "llm-gemini 0.38"
url: https://simonwillison.net/2026/Nov/18/llm-gemini/
source: simon-willison
published_at: 2026-11-18T23:59:20+00:00
fetched_at: 2026-11-19T08:17:39.690479+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Google 推出 Gemini 4 Neon，Simon Willison 更新 llm-gemini 外掛支援，並吐槽 Gemini 4 系列定價越來越難懂。 **What** llm-gemini 0.38 發布以支援 Gemini 4 Neon。目前價格（每百萬 token 輸入/輸出）為 Neon $3/$15、Carbon $2/$10（半價優惠）、Hydrogen $1.50/$7.50；Carbon 將於 12 月 1 日漲為 $4/$20，屆時 Neon 會落在 Carbon 與 Hydrogen 之間。作者另以 pelican 測試 Neon 三種推理等級，認為其表現優於 Hydrogen、劣於 Carbon，並在 Google Antigravity 以 extra 等級做了 three.js 機甲動畫測試。"
key_points:
  - "Gemini 4 Neon 定價 $3/$15（每百萬 token 輸入/輸出）；Carbon 現為半價 $2/$10，12/1 起漲為 $4/$20；Hydrogen $1.50/$7.50"
  - "Gemini 4 目前價序因 Carbon 優惠而與標準價序不同，作者認為 Neon 讓定價更混亂，且發布圖中未提 Argon"
  - "pelican 測試中 Neon 優於 Hydrogen、劣於 Carbon；llm-gemini 0.38 為對應外掛版本"
tags: [gemini-4-neon, llm-gemini, pricing, simon-willison, pelican-benchmark]
topics: [foundation_models.gemini, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-gemini 0.38

Google 推出 Gemini 4 Neon，Simon Willison 更新 llm-gemini 外掛支援，並吐槽 Gemini 4 系列定價越來越難懂。

**What** llm-gemini 0.38 發布以支援 Gemini 4 Neon。目前價格（每百萬 token 輸入/輸出）為 Neon $3/$15、Carbon $2/$10（半價優惠）、Hydrogen $1.50/$7.50；Carbon 將於 12 月 1 日漲為 $4/$20，屆時 Neon 會落在 Carbon 與 Hydrogen 之間。作者另以 pelican 測試 Neon 三種推理等級，認為其表現優於 Hydrogen、劣於 Carbon，並在 Google Antigravity 以 extra 等級做了 three.js 機甲動畫測試。

### 重點
- Gemini 4 Neon 定價 $3/$15（每百萬 token 輸入/輸出）；Carbon 現為半價 $2/$10，12/1 起漲為 $4/$20；Hydrogen $1.50/$7.50
- Gemini 4 目前價序因 Carbon 優惠而與標準價序不同，作者認為 Neon 讓定價更混亂，且發布圖中未提 Argon
- pelican 測試中 Neon 優於 Hydrogen、劣於 Carbon；llm-gemini 0.38 為對應外掛版本

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/18/llm-gemini/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-gemini 0.38 
 Today Google introduced Gemini 4 Neon . I wrote recently about how confusing the pricing for the Gemini 4 series was - Neon has somehow made this even worse. 
 Previously the Gemini 4 lineup was Hydrogen, Argon, and Carbon - where Argon and Carbon were the same price , and Hydrogen was 3/4 of that price now but will be 1/4 of that price when the other two double an 1st December once their initial discount pricing expires. 
 The Neon announcement pretends that Argon doesn't exist. Here's their new image explaining the model line-up: 
 
 So the lineup now, from most to least expensive, is Carbon, Neon, Hydrogen. 
 Except Carbon is currently half price, so right now Neon ($3/million input, $15/million output) is the most expensive of the three - then Carbon ($2/$10), then Hydrogen ($1.50/$7.50). I guess this will make more sense when Carbon doubles to $4/$20 on December 1st. 
 I ran some pelicans through the three reasoning levels for Neon - low, medium, high. 
 I dropped Argon from my Gemini 4 comparison grid - here's the new Gemini 4 lineup, where the Neon pelicans do look better than Hydrogen and worse than Carbon: 
 
 As I've done with several recent models , I also fired the following prompt against Gemini 4 Neon on "extra" effort level in Google Antigravity: 
 
 Make a three js animation where yonkers stands up as a big mech (cool stand up motion) and stomps around manhattan and queens and Brooklyn, use openstreetmap mapping data 
 
 Here's the result . 
 
 
 
 
 
 Tags: yonkers-rising , gemini , llm , pelican-riding-a-bicycle , ai , llms , llm-release , google , generative-ai

</details>