---
id: inbox_dac638d3
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2322-simon-willison-introducing-our-smallest-most-efficient-2bb2]]"
title: "Introducing Our Smallest, Most Efficient Model: Muse Ember"
url: https://simonwillison.net/2026/Nov/10/muse-ember/
source: simon-willison
published_at: 2026-11-10T07:28:21+00:00
fetched_at: 2026-11-10T23:28:41.355550+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Meta 推出最小最便宜的推理模型，比較模型成本時要看每個任務花多少，而不是每個 token 的單價。 **Why** 推理 token 讓不同模型解同一題的 token 用量差很多，單看 per-token 價格沒有意義。 **How** 作者改看 Artificial Analysis 的 Intelligence Index vs. Cost per Task 圖，並看模型是否落在 Pareto 前緣。 **What** Meta 發布 Muse Ember 1.0，短提示價格 $0.10/$0.50（與 GPT-6 Luna、Claude Haiku 5.5 相同），支援百萬 token 輸入，長提示（>200k）漲到 $0.30/$1.50，介於另兩者之間。Meta 稱它位於 Artificial Analysis 全榜的效率前緣；有六個推理等級，作者的鵜鶘 SVG 品質與價格約 40 倍的 Muse Wonder 相當。"
key_points:
  - "Muse Ember 價格：≤200k 為 $0.10/$0.50，>200k 為 $0.30/$1.50；快取輸入 $0.004/$0.012"
  - "對照：GPT-6 Luna 門檻 272k（$0.20/$0.75）、Claude Haiku 5.5 門檻 100k（$0.50/$2.50）"
  - "比較成本應看 Cost per Task 與 Pareto 前緣，因為推理 token 讓單價失真"
tags: [muse-ember, meta, llm-pricing, artificial-analysis, small-models]
topics: [engineering.evals, product_and_org.product]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Introducing Our Smallest, Most Efficient Model: Muse Ember

Meta 推出最小最便宜的推理模型，比較模型成本時要看每個任務花多少，而不是每個 token 的單價。

**Why** 推理 token 讓不同模型解同一題的 token 用量差很多，單看 per-token 價格沒有意義。

**How** 作者改看 Artificial Analysis 的 Intelligence Index vs. Cost per Task 圖，並看模型是否落在 Pareto 前緣。

**What** Meta 發布 Muse Ember 1.0，短提示價格 $0.10/$0.50（與 GPT-6 Luna、Claude Haiku 5.5 相同），支援百萬 token 輸入，長提示（>200k）漲到 $0.30/$1.50，介於另兩者之間。Meta 稱它位於 Artificial Analysis 全榜的效率前緣；有六個推理等級，作者的鵜鶘 SVG 品質與價格約 40 倍的 Muse Wonder 相當。

### 重點
- Muse Ember 價格：≤200k 為 $0.10/$0.50，>200k 為 $0.30/$1.50；快取輸入 $0.004/$0.012
- 對照：GPT-6 Luna 門檻 272k（$0.20/$0.75）、Claude Haiku 5.5 門檻 100k（$0.50/$2.50）
- 比較成本應看 Cost per Task 與 Pareto 前緣，因為推理 token 讓單價失真

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/10/muse-ember/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Introducing Our Smallest, Most Efficient Model: Muse Ember 
Meta AI just launched their entry in the Claude Haiku/GPT Luna category: Muse Ember, which they describe as: 
 
 [...] our smallest and most efficient model designed for complex reasoning execution and the work agents repeat all day: tool calls, coding subtasks, routing, extraction, and long document parsing. 
 
 For shorter prompts it's priced the same as GPT-6 Luna and Claude Haiku 5.5 - both are $0.10/million input tokens and $0.50/million output. Today's other big model release, Claude Fable 5.2, is 80x that price at $8/$40. 
 The pricing is a little less straightforward as prompts get longer, though. Luna, Ember, and Haiku all support up to a million input tokens, but they also all have a threshold after which the price goes up. Taking that threshold into account Ember is priced between the two others: 
 
 
 
 Model 
 Prompt size 
 Input ($/M) 
 Cached input 
 Output 
 
 
 
 
 GPT-6 Luna 
 ≤272k 
 $0.10 
 $0.01 
 $0.50 
 
 
 >272k 
 $0.20 
 $0.02 
 $0.75 
 
 
 Muse Ember 1.0 
 ≤200k 
 $0.10 
 $0.004 
 $0.50 
 
 
 >200k 
 $0.30 
 $0.012 
 $1.50 
 
 
 Claude Haiku 5.5 
 ≤100k 
 $0.10 
 $0.01 
 $0.50 
 
 
 >100k 
 $0.50 
 $0.05 
 $2.50 
 
 
 

 But comparing price-per-token doesn't really make sense these days, when reasoning tokens mean that different models might use dramatically different numbers of tokens to solve the same problem. 
 For that, one measure that's useful is the Artificial Analysis. 
 
 And even more useful than that is their Intelligence Index vs. Cost per Task chart, which shows the following for those three models: 
 
 The Muse Ember models sit right on that Pareto line - the line at which you can only improve one dimension by giving up another. Meta call this out in their announcement: 
 
 It also sits on the efficiency frontier of the full Artificial Analysis leaderboard: no model scores higher for less per task. 
 
 (That grey dot on the Pareto line in the middle of the green area is GPT-6.1 Terra (low) - clearly I should be paying more attention to the Terra family!) 
 Muse Ember has six reasoning levels - minimal, low, medium, high, xhigh, and max - so I rendered six pelicans riding bicycles . The "high" reasoning level failed to return a full SVG, and the other SVGs were surprising in that the reasoning level didn't cleanly map to the visual quality of the response. 
 Here's the "max" one, but the others are worth a look too: 
 
 The Ember pelicans are comparable in quality to those I got from Muse Wonder , which is 40x the price of Muse Ember.

 Tags: ai , generative-ai , llms , meta , llm-pricing , llm-release , artificial-analysis , muse

</details>