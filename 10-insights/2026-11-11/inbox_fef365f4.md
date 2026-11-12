---
id: inbox_fef365f4
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0253-tomasz-tunguz-who-captures-the-most-margin-in-ai-83d0]]"
title: "Who Captures the Most Margin in AI?"
url: https://tomtunguz.com/who-captures-the-most-margin-in-ai/
source: tomasz-tunguz
published_at: 2026-11-11T00:00:00+00:00
fetched_at: 2026-11-12T02:59:47.952566+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 AI 產業鏈從電廠到應用拆成五層，用同一單位算出各層分到多少毛利。 **Why** 各層計價單位不同（度電、GPU 小時、完成任務），很難直接比較誰賺最多。 **How** 把每一層正規化成每瓦每年美元（$/w/yr），依公開財報與建模假設畫出 waterfall。 **What** 以應用層毛利 40% 計，毛利池分配為電力 3%、資料中心 5%、neocloud 28%（GPU 折舊前）、inference 24%、應用 40%。CoreWeave 新的四到五年合約已漲到每 MW 每年 $20–25m，是目前混合費率 $9/w/yr 的兩倍以上。CoreWeave 與 Nebius 以併購向上整合。作者註明估算誤差大，多項數字來自模型假設而非審計揭露。"
key_points:
  - "毛利池分配（應用層毛利 40% 情境）：電力 3%、資料中心 5%、neocloud 28%（折舊前）、inference 24%、應用 40%"
  - "CoreWeave 新四到五年合約每 MW 每年 $20–25m，對比目前混合費率 $9/w/yr；Anthropic S-1/A 揭露短期 burst 算力 $7–13/GPU-hour"
  - "垂直整合：CoreWeave 併購 Weights & Biases（$1.03b）、OpenPipe、Marimo、Monolith AI（$185m）；Nebius 2026 年已併購四家公司"
tags: [ai-value-chain, gross-margin, coreweave, compute-pricing, vertical-integration]
topics: [product_and_org.product, engineering.inference]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Who Captures the Most Margin in AI?

把 AI 產業鏈從電廠到應用拆成五層，用同一單位算出各層分到多少毛利。

**Why** 各層計價單位不同（度電、GPU 小時、完成任務），很難直接比較誰賺最多。

**How** 把每一層正規化成每瓦每年美元（$/w/yr），依公開財報與建模假設畫出 waterfall。

**What** 以應用層毛利 40% 計，毛利池分配為電力 3%、資料中心 5%、neocloud 28%（GPU 折舊前）、inference 24%、應用 40%。CoreWeave 新的四到五年合約已漲到每 MW 每年 $20–25m，是目前混合費率 $9/w/yr 的兩倍以上。CoreWeave 與 Nebius 以併購向上整合。作者註明估算誤差大，多項數字來自模型假設而非審計揭露。

### 重點
- 毛利池分配（應用層毛利 40% 情境）：電力 3%、資料中心 5%、neocloud 28%（折舊前）、inference 24%、應用 40%
- CoreWeave 新四到五年合約每 MW 每年 $20–25m，對比目前混合費率 $9/w/yr；Anthropic S-1/A 揭露短期 burst 算力 $7–13/GPU-hour
- 垂直整合：CoreWeave 併購 Weights & Biases（$1.03b）、OpenPipe、Marimo、Monolith AI（$185m）；Nebius 2026 年已併購四家公司

**原文：** [tomasz-tunguz](https://tomtunguz.com/who-captures-the-most-margin-in-ai/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Read on tomtunguz.com → Who captures the most margin in the AI value chain? 1 Public filings now let us trace the dollars from the power plant to the agent. 
 

 Five layers make up the chain : 
 
 Power plant : produces the electricity. 2 
 Data center operator : builds the building, connects the power & provides a shell. 3 
 Neocloud : buys the GPUs & manages them. 4 
 Inference vendor : runs the software to power AI. 5 
 AI application : sells software to a customer. 
 
 Each layer bills in a different unit : utilities sell kilowatt-hours, neoclouds rent GPU-hours (an hour of a GPU’s time) & applications price completed tasks. Normalizing every step to dollars per watt per year ($/w/yr) puts the whole stack on one scale. 6 
 Here is the waterfall : 
 

 At a 40% application gross margin, the total gross profit pool divides from left to right as : 
 
 Power : 3% 
 Data center : 5% 
 Neocloud : 28% (before GPU depreciation) 7 
 Inference : 24% 
 Application : 40% 
 
 Three implications follow from the chain : 
 1. Rising compute prices will test who holds pricing power. From Anthropic to CoreWeave, compute prices are climbing. Anthropic’s Form S-1/A discloses short-term burst compute reaching $13 per GPU-hour. 8 On CoreWeave’s Q3 earnings call, CEO Michael Intrator confirmed the shift in contract rates : 
 
 “Selling capacity at more than $40m per megawatt annually while pricing for new infrastructure on four & five year contracts is moving to $20m to $25m per megawatt.” 9 
 
 At $20m to $25m per megawatt ($20 to $25/w/yr), new multi-year compute contracts price at more than double CoreWeave’s $9/w/yr blended fleet today. If the application can charge the end user more because of its effectiveness, higher compute costs cascade through. Otherwise, neoclouds, inference providers & applications fight over a fixed pool. 
 2. Different applications will command varying pricing power as a function of their ROI. An AI that saves 30% does not command the same pricing power as one that saves 70%. Techniques like small models, fine-tuning & routing will help sustain margins. Unlike the SaaS era, different vertical software markets will support varying gross profit pools. 
 3. Vertical integration is already consolidating margin. Companies across the stack are absorbing neighboring layers to capture adjacent margin. CoreWeave acquired Weights & Biases ($1.03b), OpenPipe, Marimo & Monolith AI ($185m) to move up into training, evaluation & enterprise workflows. 10 Nebius has spent more than $1b in 2026 acquiring four companies across search, model optimization, cold-start scaling & orchestration to build its Token Factory. 11 Owning multiple layers lets an integrated provider absorb price swings that squeeze standalone vendors. 
 No layer in AI is static. As market power shifts from one layer to the next, though, understanding these shifts will explain where competition is fiercest & where M&A will concentrate. 
 
 
 
 
 See Tomasz Tunguz, Startup Best Practices 26 : Choosing Your Startup’s Competitive Strategy , May 26, 2017, & How to Analyze Your Startup Like a VC in 15 Minutes or Less , June 24, 2013, on mapping industry value chains & where margin accrues across layers. ↩︎ 
 
 
 Core Scientific SEC filings report pass-through electricity at 6.6 to 7.1 cents per kWh (West Texas closer to 5 cents). One watt-year is 8.76 kWh ; at an estimated 1.3 PUE, annual power cost is $0.75 to $0.80/w/yr. Because utility gross margins are not broken out per data center, $0.80/w/yr represents utility revenue (cost basis to the stack). ↩︎ 
 
 
 CoreWeave wholesale colocation leases with Core Scientific run $100 to $115 per kW-month on 12-year take-or-pay terms, with effective all-in rent near $165/kw-month ($1.98/w/yr). CBRE (North America Data Center Trends H1 2026, August 27, 2026) puts primary North American wholesale asking rates at $204.69/kw-month for 250 to 500kw deployments ($196.25 in 2025) & $165.31/kw-month for 10mw+ blocks ($1.98/w/yr). ↩︎ 
 
 
 CoreWeave Q3 2026 earnings release, 10 November 2026 : revenue of $3.661b (+168% YoY), GAAP operating income of $207m (6% margin), adjusted operating income of $379m (10% margin), Adjusted EBITDA of $2.26b (62% margin), depreciation & amortization of $1.89b, net interest expense of $846m & GAAP net loss of $709m. Active power rose from 1.5gw at Q2 end to above 1.7gw at Q3 end (contracted power above 4.6gw, backlog $132.5b). Annualized Q3 revenue ($14.64b) across ~1.6gw of period-average active power equals $9.15m per megawatt per year, or $9.15/w/yr. ↩︎ 
 
 
 Modeled on a 552b-parameter mixture-of-experts model (8b active input, 16b active output) on GB300 NVL72 racks (72 GPUs at 150 to 180kw) with 87% to 90% prompt cache hit rates & 65% billing utilization, paying $9/w/yr for compute & billing $15/w/yr ($23.08 per utilized watt). ↩︎ 
 
 
 This estimate carries meaningful error across workloads & utilization rates. Converting kWh, $/kw-month leases, $/GPU-hour compute, per-million-token inference & per-task agent pricing onto a single $/w/yr denominator relies on modeled approximations rather than audited disclosures : quarterly starting active power, facility PUE (1.2 to 1.45), rack power draw (150 to 180kw), billing utilization (65%) & cache hit rates (87% to 90%, where cached reads still consume HBM capacity & bandwidth). ↩︎ 
 
 
 Two accounting boundaries shape the waterfall : GPU hardware & frontier model weights sit inside the capital & operating lines rather than as separate recurring service bars. CoreWeave’s +$7.00/w/yr is pre-depreciation (reflecting only ~$2/w/yr of shell & power ; company-wide Adjusted EBITDA is 62% after ~$1/w/yr of other operating costs). Upfront GPU capex of $35 to $50/w depreciated over six years adds $6 to $8/w/yr in capital charges : where Nvidia’s ~75% hardware gross margin lives : reducing CoreWeave’s post-depreciation gross profit at today’s $9/w/yr blended rate to $0 to $2/w/yr (Q3 D&A alone was $1.89b, 52% of revenue). Likewise, the inference bar models an open-weight model rather than a proprietary frontier lab API. ↩︎ 
 
 
 Anthropic, PBC Form S-1/A, filed 2 November 2026 : Q3 2026 short-term burst compute commitments reached $7 to $13 per GPU-hour across $5.0b of quarterly short-term spend. ↩︎ 
 
 
 Michael Intrator, Chief Executive Officer, CoreWeave Q3 2026 earnings call, 10 November 2026 (units formatted to $40m & $20m to $25m from transcript’s “40 million” & “20 to 25 million”). ↩︎ 
 
 
 CoreWeave Form 10-K for the year ended 31 December 2025 (filed 2 March 2026, Note 4) : CoreWeave closed four software acquisitions in 2025 to move up the stack : Weights & Biases ($1.029b total purchase consideration, closed May 5, 2025), OpenPipe (September 2025), Marimo (October 2025) & Monolith AI ($185m in convertible notes, closed November 5, 2025). ↩︎ 
 
 
 Nebius Group 2026 software transactions : Tavily (announced February 10, 2026 ; $275m initial consideration, up to $400m with earnouts), Eigen AI (announced May 1, 2026 ; ~$643m in cash & stock, closed June 10, 2026), Clarifai core research & engineering team hire plus perpetual inference & orchestration IP license (May 12, 2026), & Inferize (acquired October 1, 2026 ; estimated $100m to $150m per CTech ). ↩︎

</details>