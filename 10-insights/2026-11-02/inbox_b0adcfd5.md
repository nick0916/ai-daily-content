---
id: inbox_b0adcfd5
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2326-tomasz-tunguz-the-four-questions-of-ai-f93c]]"
title: "The Four Questions of AI"
url: https://tomtunguz.com/the-four-questions-of-ai/
source: tomasz-tunguz
published_at: 2026-11-02T00:00:00+00:00
fetched_at: 2026-11-02T23:31:36.869543+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 AI 產業拆成應用、harness、模型、資料中心四層，每層各有一個決定勝負的關鍵問題，而且四層互相牽動。 **Why** 各層經濟學彼此耦合：上層獲利支撐下層的 GPU 漲價與融資成本，新架構又能降低下層的資源需求，單看一層會誤判整體走向。 **How** 作者逐層列出問題，並用腳註引用 benchmark、財報與市場資料佐證，最後以雙擺（double pendulum）比喻四層是簡單部件組成的混沌系統。 **What** 應用層：薄包裝會被模型吸收，問題是 UI 是否存續。Harness 層：Endor Labs 基準中 GPT-5.5 在 Codex 得 61.5%、在 Cursor 得 87.2%，Claude Opus 4.7 在 Claude Code 87.2%、在 Cursor 91.1%；聰明的 harness 可降成本 71%、毛利從 38% 升至 75%。模型層：約 83% 的 agent 任務改走較小或領域模型，訓練成本是否回本成疑。資料中心層：AI 債務約需 $4t，Ornn B300 指數 $12.29/GPU-hour。"
key_points:
  - "Harness 層證據：同一週內 OpenAI 與 Anthropic 模型在 Cursor 的分數都高於在自家 harness（GPT-5.5：Cursor 87.2% vs Codex 61.5%；Opus 4.7：Cursor 91.1% vs Claude Code 87.2%）；輸入 context 佔 token 達 85.7%–98.2%，UC Berkeley HarnessTax 研究顯示同樣 SWE-bench 任務成本降 71%"
  - "模型層：約 83% 的 agent 任務路由到較小或領域微調模型；單一研究員搭配 coding agent 以不到 $10m 預訓練出 Mirendil-Base；109M 的 text JEPA 以少 42 倍資料勝過 72B LLM（對齊視覺編碼器的指標）"
  - "資料中心層：未來五年約需 $4t 新債，相當美國市政債市場 91%；CoreWeave 五年期 CDS 1,090 bps、Oracle 322 bps、Meta 108 bps；混凝土成本漲 3 倍"
tags: [ai-stack, harness, moat, gpu-economics, ai-financing]
topics: [product_and_org.product, engineering.architecture, research.training]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Four Questions of AI

把 AI 產業拆成應用、harness、模型、資料中心四層，每層各有一個決定勝負的關鍵問題，而且四層互相牽動。

**Why** 各層經濟學彼此耦合：上層獲利支撐下層的 GPU 漲價與融資成本，新架構又能降低下層的資源需求，單看一層會誤判整體走向。

**How** 作者逐層列出問題，並用腳註引用 benchmark、財報與市場資料佐證，最後以雙擺（double pendulum）比喻四層是簡單部件組成的混沌系統。

**What** 應用層：薄包裝會被模型吸收，問題是 UI 是否存續。Harness 層：Endor Labs 基準中 GPT-5.5 在 Codex 得 61.5%、在 Cursor 得 87.2%，Claude Opus 4.7 在 Claude Code 87.2%、在 Cursor 91.1%；聰明的 harness 可降成本 71%、毛利從 38% 升至 75%。模型層：約 83% 的 agent 任務改走較小或領域模型，訓練成本是否回本成疑。資料中心層：AI 債務約需 $4t，Ornn B300 指數 $12.29/GPU-hour。

### 重點
- Harness 層證據：同一週內 OpenAI 與 Anthropic 模型在 Cursor 的分數都高於在自家 harness（GPT-5.5：Cursor 87.2% vs Codex 61.5%；Opus 4.7：Cursor 91.1% vs Claude Code 87.2%）；輸入 context 佔 token 達 85.7%–98.2%，UC Berkeley HarnessTax 研究顯示同樣 SWE-bench 任務成本降 71%
- 模型層：約 83% 的 agent 任務路由到較小或領域微調模型；單一研究員搭配 coding agent 以不到 $10m 預訓練出 Mirendil-Base；109M 的 text JEPA 以少 42 倍資料勝過 72B LLM（對齊視覺編碼器的指標）
- 資料中心層：未來五年約需 $4t 新債，相當美國市政債市場 91%；CoreWeave 五年期 CDS 1,090 bps、Oracle 322 bps、Meta 108 bps；混凝土成本漲 3 倍

**原文：** [tomasz-tunguz](https://tomtunguz.com/the-four-questions-of-ai/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

There are 4 layers in the AI stack, each with a fundamental question before it. 
 

 Application 
 Breakout hits appear overnight. The next model release can erase them just as fast. Thin wrappers die when the model absorbs their feature. To build a moat, app companies must decide whether to build a brand, disrupt incumbents through pricing, develop their own models, or expand faster than competitors. 
 Agents do the work with headless software. Will a user interface survive, or do all applications collapse into middleware harnesses 1 ? 
 Harness & Context 
 If applications collapse into middleware, the fight moves to who owns the harness. Model makers claim their native harness wins. The benchmarks say otherwise. In the same week, both OpenAI & Anthropic models scored higher in Cursor than in their creators’ own harnesses 2 . Because input context is up to 98% of all tokens 2 , a smart harness cuts the cost of the same answer by 71% & lifts gross margin from 38% to 75% 3 . 
 Beyond the model makers, enterprises are starting to lay claim to the harness to build corporate sovereign AI 4 . No CIO wants to ship company secrets out the door in a prompt. Owning the context layer lets a company keep its memory & permissions in house while swapping models underneath. 
 Model 
 For foundation models, the question is at what point training costs don’t pay back. Training a state-of-the-art model costs billions 5 . Recursive self-improvement, AI models training better AI, has not yet bailed out the big labs. AI writes 75% of Google DeepMind’s production code, yet Google sees no end-to-end speedup in AI research 6 . 
 On the demand side, Rich Sutton’s Bitter Lesson argues that general models scaled with massive compute always win 7 . Yet SOTA models are losing token share on public gateways because they cost too much to run 8 . About 83% of agent tasks now route to smaller or domain-specific models fine-tuned to do one job for a fraction of the bill 9 . 
 Challengers are attacking the training bill through process & architecture. One startup used coding agents to pre-train a competitive coding model with a single researcher for under $10m 10 . New architectures like diffusion models 11 & JEPA, where a 109m model beat 72b LLMs with 42x less data 12 , bypass brute-force scaling. 
 Still, the bull case for scaling the frontier sits in Anthropic’s S-1. Opus 5.5 cut customer cost per task by 40%, & when Opus 4.5 delivered more capability at a lower cost per task than Opus 4.1, Jevons paradox kicked in & sequential quarterly revenue growth accelerated from 48% to 132% 13 . 
 Data Center 
 Below the models, the question is whether credit & power can keep up with GPU demand. With concrete prices up 3x, electrical grids strained, & backlogs on turbines, generators, & reciprocating engines, the answer for now is no 14 . 
 Unrestrained growth in AI requires $4t in new debt over five years, making the AI credit market larger than global private credit & equal to 91% of the US municipal bond market 15 . Are there enough lenders left at attractive rates? Risk strains insurance costs. Five-year credit default swap spreads have hit records from Meta (108 bps) to Oracle (322 bps) & CoreWeave (1,090 bps) 16 . 
 On the ground, local politics & grid delays are blocking new sites, while Ornn’s B300 index has climbed to $12.29 per GPU-hour (~20% CMGR since June) 17 . 
 Meanwhile, three open questions hang over the math : whether cash flows match the duration of twenty-year debt & leases 15 , whether GPUs last five years, & whether the price of a GPU-hour will increase or decrease 18 . 
 How the Layers Interplay 
 None of these four questions stands alone. Applications that generate tremendous profits at the top can sustain inflation in GPU prices & higher borrowing costs at the bottom. New, more efficient architectures 19 can decrease the need for concrete & copper. Surging GPU prices can swing the economics of the whole stack. 
 Like a double pendulum 20 , the four layers form a coupled system : simple in each part, yet complex, chaotic, & unpredictable in motion. 
 
 
 
 
 A harness is the software runtime around the model, such as Claude Code, Codex, or Cursor, that governs what context flows into the prompt, which tools the agent calls, & how session trajectories are cached & logged. See Tomasz Tunguz, The Harness Is the New Battleground , July 14, 2026. ↩︎ 
 
 
 Tomasz Tunguz, Aftermarket Harnesses , July 28, 2026, citing Endor Labs’ Agent Security League benchmark (GPT-5.5 scoring 61.5% in OpenAI’s Codex vs. 87.2% in Cursor ; Claude Opus 4.7 scoring 87.2% in Claude Code vs. 91.1% in Cursor) & OpenRouter token composition data (input tokens representing 85.7% to 98.2% of volume). ↩︎ ↩︎ 
 
 
 Tomasz Tunguz, The Harness Margin Opportunity , September 17, 2026, citing UC Berkeley’s HarnessTax study (71% lower cost for the same resolved SWE-bench task with no statistically significant quality difference across 42 comparisons) & AI associate contract gross-margin modeling (38% vs. 75% on a $250k contract). ↩︎ 
 
 
 Tomasz Tunguz, The Price of Entry to the Frontier , August 31, 2026, on enterprise data sovereignty mandates, Zero Data Retention policies, & model access segmentation. ↩︎ 
 
 
 Frontier training & R&D scale : Anthropic’s S-1 (filed October 26, 2026) discloses $8.1b in FY2025 operating losses & $637b in total compute commitments ( Anthropic S-1 Analysis ), while OpenAI projects $278b in cumulative cash burn through 2030 & Epoch AI estimates individual next-generation frontier training runs crossing $1b+ as training compute grows ~5x per year ( Epoch AI ). ↩︎ 
 
 
 Google DeepMind, Gemini 4 Argon Safety & Security Report, October 2026 : AI generates more than 75% of DeepMind production code & fully delegated pull requests rose from 7.5% to 11.9% over five months, with no significant end-to-end acceleration of AI research timelines. ↩︎ 
 
 
 Rich Sutton, The Bitter Lesson , March 13, 2019 : general methods that leverage computation ultimately beat methods that embed human domain knowledge by a large margin. ↩︎ 
 
 
 Tomasz Tunguz, The Most Important Market in AI Is the Middle , September 23, 2026, & Honestly, Who Buys SOTA? , August 14, 2026 : 84% of tokens on OpenRouter are not state of the art, Anthropic’s flagship Fable 5.1 captured only 3.7% of gateway spending in its first twelve days (while its predecessor fell from 13.2% to 4.9% within a month), & among large corporate accounts frontier models fell from 53% of token consumption in early August to 45% by September. ↩︎ 
 
 
 Tomasz Tunguz, The Most Important Market in AI Is the Middle , September 23, 2026, & 9 Observations Using AI Agents , 2026 : Cursor’s Composer 2 fine-tuned open-weight Kimi K2.5 to cut costs 86% vs. its prior model, Harvey fine-tuned a domain model to cut cost per cell 55% vs. Sonnet 5 while outscoring Fable 5, & an 8b Qwen 3 model fine-tuned for task classification beat zero-shot GPT-5.2 locally on a laptop. ↩︎ 
 
 
 Mirendil, Pretraining at Scale Without a Pretraining Team , October 21, 2026 : one researcher paired with coding agents (which wrote 99% of the repository) pre-trained Mirendil-Base (100b to 500b parameters) from scratch in 3.5 months for under $10m all-in compute & token spend, beating GLM-5.3 (0.242 bits/byte), DeepSeek-V4-Pro (0.243), & Nemotron-550B (0.247) on held-out post-cutoff code repositories (averaging 0.222 bits/byte vs. 0.193 for Kimi-K3). ↩︎ 
 
 
 Diffusion language models generate & refine blocks of tokens in parallel rather than one token at a time : Inception Labs’ Mercury 2.5 (launched September 8, 2026) reaches 414 to 1,107 tokens/sec on Nvidia GPUs at $0.20/$0.75 per million tokens, roughly 9x cheaper & 3x faster than comparable autoregressive models ( Inception Labs ). ↩︎ 
 
 
 Randall Balestriero & Yann LeCun, The Platonic Representation Theorem : Joint-Embedding Predictive Architectures Converge to a Shared World Model , October 29, 2026 : by predicting compressed latent embeddings rather than surface tokens, a 109m-parameter text JEPA aligns with DINOv2 & CLIP vision encoders better than any tested autoregressive LLM up to 72b parameters (660x larger) while requiring 42x fewer training samples. ↩︎ 
 
 
 Tomasz Tunguz, Anthropic S-1 Analysis : How 7 Key Metrics Stack Up , October 26, 2026, quoting Anthropic’s S-1 : “With the release of Claude Fable 5.1 in September 2026, we reduced the cost of typical workloads by approximately 25% compared to Fable 5, with savings of up to 45% for complex coding & highly agentic tasks. Similarly, with the release of Opus 5.5 that same month, we reduced customers’ cost per task by approximately 40% compared to Opus 5.” When Opus 4.5 launched with more capability & lower cost per task than Opus 4.1, Anthropic’s sequential quarterly revenue growth accelerated from 48% to 132%. ↩︎ 
 
 
 Tomasz Tunguz, The AI Bullwhip , August 23, 2026 : data center shell & concrete construction costs have tripled to $1,033 per square foot excluding land (US Census Bureau & RSMeans Construction Cost Indices), electrical systems consume half of a $20b-per-gigawatt facility budget, generator step-up transformers average nearly three-year lead times (Wood Mackenzie), & GE Vernova & Siemens Energy have sold out gas turbine production through 2029 with order books stretching to 2031 (POWER Magazine, CNBC, & Caterpillar/Cummins data center backup generator & reciprocating engine backlog disclosures). ↩︎ 
 
 
 Tomasz Tunguz, Concrete, Silicon, & Leverage , September 4, 2026 : $4t in projected five-year AI data center debt equals 286% of US commercial paper, 143% of the global private credit market, & 91% of the $4.4t US municipal bond market, requiring $1.2t to $1.5t in annual AI revenue by 2030 to cover interest at a 3x coverage ratio. ↩︎ ↩︎ 
 
 
 Financial Times, AI debt worries spark surge in default insurance trading , October 20, 2026, citing Morgan Stanley Research ($466b YTD AI-linked debt issuance) & S&P Global Market Intelligence (5-year CDS spreads at record highs of 108 bps for Meta, 226 bps for SpaceX, 322 bps for Oracle, & 1,090 bps for CoreWeave) ; CNBC, AI debt outlook : Oracle, Alphabet & Amazon in focus , October 27, 2026. ↩︎ 
 
 
 Ornn B300 Compute Price Index (settled October 30, 2026) : the weekly B300 index stands at $12.29 per GPU-hour, up from ~$5.53 in mid-June 2026 (a 20.1% compound monthly growth rate over 4.4 months) & $10.47 on August 28, 2026 (an 8.1% CMGR over the past two months, & -$0.12 or -0.97% over the past month) ; see also Tomasz Tunguz, How GPU Prices Can Double While AI Gets Cheaper , September 28, 2026, on B200 rates doubling from $4.40 to $8.08 per hour & Oracle’s six-month force majeure delay on its New Mexico data center campus. ↩︎ 
 
 
 Even as the Ornn B300 index sits at $12.29 per GPU-hour (20.1% CMGR since June, 8.1% CMGR since August 28, & -0.97% over the past month), spot quotes in the secondary market can swing sharply : on November 1, 2026, Jaber ( @Akashi203 on X ) noted that a month after begging GPU providers for B300s at $7.90 an hour, providers were offering them at $4.60 an hour with no commitment. ↩︎ 
 
 
 DeepSeek-AI, Insights into DeepSeek-V3 : Scaling Challenges & Reflections on Hardware for AI Architectures , May 14, 2025 (Multi-head Latent Attention reducing KV cache to 70 KB per token vs. 327 KB for Qwen-2.5 72B & 516 KB for Llama-3.1 405B), & DeepSeek-V3/R1 Inference System Overview , February 28, 2025 (776b total tokens/day : 608b input & 168b output across 226.75 average H800 nodes for $87,072/day). ↩︎ 
 
 
 A double pendulum is a pendulum with a second pendulum attached to its end : although each arm obeys simple deterministic laws, the coupled system exhibits chaotic motion where tiny shifts in one arm produce large, unpredictable swings across the whole system. ↩︎

</details>