---
id: inbox_46c4521f
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/0145-simon-willison-llm-gemini-0-37-bf4f]]"
title: "llm-gemini 0.37"
url: https://simonwillison.net/2026/Nov/12/llm-gemini/
source: simon-willison
published_at: 2026-11-12T22:55:19+00:00
fetched_at: 2026-11-14T01:51:35.023275+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Gemini 4 家族新增最便宜的 Hydrogen，但定價結構讓人看不懂，價差其實不大。 **Why** Google 的 Gemini 4 三個模型定價混亂：Carbon 與 Argon 價格相同，Hydrogen 號稱低價卻只便宜 25%。 **How** Carbon 與 Argon 都將在 12 月 1 日漲價一倍，屆時 Hydrogen 才會變成 75% 折扣；Google 稱 Argon 回應更快、每輪 token 用量更少。 **What** llm-gemini 0.37 支援 Gemini 4 Hydrogen，價格為 $1.50 輸入 / $0.075 快取輸入 / $7.50 輸出（每百萬 token）。Carbon/Argon 目前 $2/$10，12 月 1 日起 $4/$20。Claude Haiku 5.5 與 GPT-6 Luna 皆為 $0.10/$0.50，Hydrogen 約為其 15 倍。Hydrogen 是新的免費層模型，也驅動 Google Search 的 AI 功能。"
key_points:
  - "Hydrogen $1.50/$7.50（每百萬 token），目前僅比 Carbon/Argon 便宜 25%；12 月 1 日兩者漲到 $4/$20 後折扣變 75%"
  - "Haiku 5.5 與 GPT-6 Luna 皆 $0.10/$0.50，Hydrogen 約貴 15 倍"
  - "Google 定位：Carbon/Argon 負責架構判斷，Hydrogen 當多模型流程中的高效率執行引擎，也是新免費層與 Search AI 模型"
tags: [gemini-4, gemini-hydrogen, llm-pricing, llm-gemini, multi-model]
topics: [foundation_models.gemini, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-gemini 0.37

Gemini 4 家族新增最便宜的 Hydrogen，但定價結構讓人看不懂，價差其實不大。

**Why** Google 的 Gemini 4 三個模型定價混亂：Carbon 與 Argon 價格相同，Hydrogen 號稱低價卻只便宜 25%。

**How** Carbon 與 Argon 都將在 12 月 1 日漲價一倍，屆時 Hydrogen 才會變成 75% 折扣；Google 稱 Argon 回應更快、每輪 token 用量更少。

**What** llm-gemini 0.37 支援 Gemini 4 Hydrogen，價格為 $1.50 輸入 / $0.075 快取輸入 / $7.50 輸出（每百萬 token）。Carbon/Argon 目前 $2/$10，12 月 1 日起 $4/$20。Claude Haiku 5.5 與 GPT-6 Luna 皆為 $0.10/$0.50，Hydrogen 約為其 15 倍。Hydrogen 是新的免費層模型，也驅動 Google Search 的 AI 功能。

### 重點
- Hydrogen $1.50/$7.50（每百萬 token），目前僅比 Carbon/Argon 便宜 25%；12 月 1 日兩者漲到 $4/$20 後折扣變 75%
- Haiku 5.5 與 GPT-6 Luna 皆 $0.10/$0.50，Hydrogen 約貴 15 倍
- Google 定位：Carbon/Argon 負責架構判斷，Hydrogen 當多模型流程中的高效率執行引擎，也是新免費層與 Search AI 模型

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/12/llm-gemini/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-gemini 0.37 
 Google launched Gemini 4 Hydrogen today - the lowest cost member of the Gemini 4 family. 
 It's actually not too far off the price of its much bigger siblings, Carbon and Argon. I'm finding Gemini 4's pricing really confusing. Here's the pricing scheme: 
 
 
 
 Model 
 Dates 
 Input ($/M) 
 Cached input 
 Output 
 
 
 
 
 Gemini 4 Carbon 
 Through Nov 30, 2026 
 $2.00 
 $0.10 
 $10.00 
 
 
 From Dec 1, 2026 
 $4.00 
 $0.20 
 $20.00 
 
 
 Gemini 4 Argon 
 Through Nov 30, 2026 
 $2.00 
 $0.10 
 $10.00 
 
 
 From Dec 1, 2026 
 $4.00 
 $0.20 
 $20.00 
 
 
 Gemini 4 Hydrogen 
 
 $1.50 
 $0.075 
 $7.50 
 
 
 

 Carbon and Argon are the same price , and both are scheduled to double in price on December 1st. If they're the same price, why have two different models? Google says that Argon "delivers Gemini 4 intelligence with faster responses and lower token spend per turn compared to Gemini 4 Carbon" - so it may be priced the same, but it will use less tokens per task. 
 Hydrogen, supposedly the cheap model, is currently only a 25% discount on its more capable peers. The Hydrogen price will make more sense after December 1st, when it will represent a 75% discount. It's still considerably more expensive than Claude Haiku 5.5 and GPT-6 Luna - they're both $0.10/$0.50, so Hydrogen is 15x that. 
 I had Hydrogen generate some pelicans . Here's a full comparison grid showing the pelicans for all three members of the Gemini 4 family at their three supported effort levels: 
 
 Considering how close they are in price, the difference in pelican quality for Hydrogen is quite stark. 
 Here's how Google describe Hydrogen's intended position in their mix of models: 
 
 In real-world software development, while teams rely on frontier models like Carbon and Argon for deep architectural judgment when designing systems or untangling subtle bugs, they still need a fast, disciplined execution model for writing code, running tests, and verifying changes. Hydrogen is built to stand on its own as a model for everyday work — or to pair with Carbon and Argon as the high-efficiency execution engine in multi-model workflows. 
 
 Most notably, Hydrogen is the new free tier model, and is the model that will power AI features in Google Search. 
 
 
 Tags: gemini , llm , google , pelican-riding-a-bicycle , llm-pricing , ai , llms

</details>