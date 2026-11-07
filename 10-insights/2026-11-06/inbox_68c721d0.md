---
id: inbox_68c721d0
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0141-tomasz-tunguz-a-90-key-into-your-company-s-secrets-4861]]"
title: "A $90 Key into Your Company's Secrets"
url: https://tomtunguz.com/a-90-dollar-key-into-your-companys-secrets/
source: tomasz-tunguz
published_at: 2026-11-06T00:00:00+00:00
fetched_at: 2026-11-07T01:46:35.448090+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 讓駭入企業網路的成本五個月跌 99%，資安預算得跟著算算力帳。 **Why** 自主 AI 攻擊成為主要風險後，攻守雙方比的是誰能投入更多 AI 算力，防守方每一塊錢攻擊算力要用多少防禦算力來抵銷，是比攻擊方更難的方程式。 **How** 作者以期望值算攻擊方的帳：花 $1m token 攻擊有 1% 機率拿到 $1b 的目標，期望值 $10m；花同樣算力攻擊 5% 機率拿到 $500k 的目標則虧損。便宜的防禦過濾器擋掉低成本雜訊，理性的攻擊者會把 token 集中在最大的資產負債表上。防守方的算力需求被速度、規模、廣度三個乘數放大。 **What** 同一個 32 步、20 台伺服器的模擬英國企業網路入侵，4 月 BIS 估價 $5k–$10k，6 月 Claude Mythos 5 降到 $770，7 月 Claude Opus 5 降到 $385，Zhipu 開源權重的 GLM-5.3 僅 $90。SOC 每天面對 4,400 多則警報，AI 自主調查每則約 $2 算力；2026 年 7 月 Hugging Face 入侵中 700 個 agent 在四天半內執行 17,600 次動作並取得 136 把 production key。作者結論是 CISO 要買足算力並轉成防禦 token，把攻擊者的期望值壓到零以下。"
key_points:
  - "同一入侵任務成本：4 月 $5k–$10k → Claude Mythos 5 $770（6 月）→ Claude Opus 5 $385（7 月）→ GLM-5.3 $90，作者依 100m token 與 7:2:1 比例換算"
  - "攻擊者看期望值：$1m 算力打 1% 機率 $1b 目標期望值 $10m，打 5% 機率 $500k 目標則虧 $975k，攻擊會集中在最大目標"
  - "防守三乘數：速度（CrowdStrike 平均 breakout 29 分鐘、最快 27 秒）、規模（Hugging Face 事件 700 agent、76% 新攻擊路徑僅 AI 蜂群可行）、廣度（非人類身分與員工比 82:1）"
tags: [ai-cyber-offense, security-economics, glm-5-3, claude-mythos, soc-automation]
topics: [security, foundation_models.open_weights]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## A $90 Key into Your Company's Secrets

AI 讓駭入企業網路的成本五個月跌 99%，資安預算得跟著算算力帳。

**Why** 自主 AI 攻擊成為主要風險後，攻守雙方比的是誰能投入更多 AI 算力，防守方每一塊錢攻擊算力要用多少防禦算力來抵銷，是比攻擊方更難的方程式。

**How** 作者以期望值算攻擊方的帳：花 $1m token 攻擊有 1% 機率拿到 $1b 的目標，期望值 $10m；花同樣算力攻擊 5% 機率拿到 $500k 的目標則虧損。便宜的防禦過濾器擋掉低成本雜訊，理性的攻擊者會把 token 集中在最大的資產負債表上。防守方的算力需求被速度、規模、廣度三個乘數放大。

**What** 同一個 32 步、20 台伺服器的模擬英國企業網路入侵，4 月 BIS 估價 $5k–$10k，6 月 Claude Mythos 5 降到 $770，7 月 Claude Opus 5 降到 $385，Zhipu 開源權重的 GLM-5.3 僅 $90。SOC 每天面對 4,400 多則警報，AI 自主調查每則約 $2 算力；2026 年 7 月 Hugging Face 入侵中 700 個 agent 在四天半內執行 17,600 次動作並取得 136 把 production key。作者結論是 CISO 要買足算力並轉成防禦 token，把攻擊者的期望值壓到零以下。

### 重點
- 同一入侵任務成本：4 月 $5k–$10k → Claude Mythos 5 $770（6 月）→ Claude Opus 5 $385（7 月）→ GLM-5.3 $90，作者依 100m token 與 7:2:1 比例換算
- 攻擊者看期望值：$1m 算力打 1% 機率 $1b 目標期望值 $10m，打 5% 機率 $500k 目標則虧 $975k，攻擊會集中在最大目標
- 防守三乘數：速度（CrowdStrike 平均 breakout 29 分鐘、最快 27 秒）、規模（Hugging Face 事件 700 agent、76% 新攻擊路徑僅 AI 蜂群可行）、廣度（非人類身分與員工比 82:1）

**原文：** [tomasz-tunguz](https://tomtunguz.com/a-90-dollar-key-into-your-companys-secrets/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The cost of breaking into a corporate network with AI has fallen 99% in five months, & corporate security budgets are racing to catch up. 
 
 Goldman executives have discussed how the firm could soon be on track to spend as much or more on AI for security than it spends on AI coding tools. 1 , 2 
 
 Security has been a collection of layers of defense, each an insurance policy against a particular kind of attack. 1 As autonomous AI threats become the predominant risk, both attackers & defenders are competing on how much AI compute they can deploy. 
 An attacker’s math is an expected-value calculation on compute. Spend $1m of AI tokens trying to break into a bank with a 1% chance at a $1b payout, & the expected value is $10m : a $9m expected profit. Spend that same compute on a 5% chance at a $500k payout, & the expected return is $25k : a $975k loss. Because cheap defensive filters block low-effort noise, rational attackers stop spraying small targets & concentrate their tokens on the largest balance sheets. 
 Defenders face a harder equation : how much defensive AI it takes to neutralize each dollar of offensive AI. 
 In April, Anthropic & OpenAI tested whether Claude Mythos Preview & GPT-5.5 could break into a simulated British corporate network : a 32-step hack across 20 servers that takes a human expert 20 hours. 3 , 4 Both models took over the network without human help, & the Bank for International Settlements priced the break-in at $5k to $10k. 3 
 Five months later, the price of that same break-in has fallen 99%. Claude Mythos 5 dropped the cost to $770 in June, Claude Opus 5 to $385 in July, & Zhipu’s open-weight GLM-5.3 matches Mythos’s exploit rate for $90 : one-sixtieth of April’s frontier cost. 5 
 
 

 In the security operations center, AI agents relieve overwhelmed human teams who face more than 4,400 alerts a day & historically lacked the hours to examine two-thirds of them : autonomous investigations compress a 70-minute manual review into minutes for about $2 of compute per alert, freeing analysts to focus on real intrusions. 6 
 Yet the cost ratio still starts tilted toward the attacker, because the SOC must inspect every alert, every hour. 3 , 7 
 Three multipliers compound that defensive compute requirement : 
 First, speed : Glean CISO Sunil Agrawal notes that AI compresses intrusion response from months to minutes, while CrowdStrike records average breakout times of 29 minutes & a fastest of 27 seconds. 8 , 9 
 Second, scale : in the July 2026 intrusion at Hugging Face, a swarm of 700 AI agents coordinated across four & a half days, exchanging 70,000 messages & executing 17,600 actions until they harvested 136 production keys, & Cogent Research finds 76% of new monthly enterprise attack paths (up 386% year over year) are viable only for parallel AI swarms. 10 
 Third, breadth : non-human identities already outnumber employees 82 to 1, & as enterprise agent fleets scale to 100x headcount, every new agent expands the surface area to defend. 11 , 12 
 The CISO’s job is no longer stacking per-seat insurance policies. It is maximizing the efficiency & effectiveness of the security stack : buying enough compute, & converting it into enough defensive tokens, to drive the attacker’s expected value below zero. 
 
 
 
 
 The Third Product-Market Fit in AI , tomtunguz.com. ↩︎ ↩︎ 
 
 
 “Nobody’s Ready” : AI-Found Bugs Spark Corporate Security Spending Spree , The Information. ↩︎ 
 
 
 Iñaki Aldasoro, Raphael Auer, Jon Frost, & Fernando Pérez-Cruz, BIS Bulletin No. 129 : A Mythos moment? Frontier AI & cyber risk , Bank for International Settlements, July 20, 2026 ( PDF ). Source for the 100m-token attack chain, the $5k to $10k frontier cost range, & the 32-of-32 cyber-range takeover by Claude Mythos Preview & GPT-5.5. ↩︎ ↩︎ ↩︎ 
 
 
 UK AI Security Institute, How fast is autonomous AI cyber capability advancing? , May 13, 2026, & Our evaluation of Claude Mythos Preview’s cyber capabilities , April 13, 2026 (32-step simulated corporate network across 4 subnets & ~20 hosts, estimated at 20 human expert hours). ↩︎ 
 
 
 Anthropic, GLM-5.3 & the spread of advanced cyber capabilities , September 29, 2026 (GLM-5.3 builds end-to-end Chrome V8 exploits on ExploitBench in 50 of 410 attempts versus 56 of 410 for Claude Mythos Preview) ; Jaeho Lee & Alexander Barry, Open-weight AI models are 6-7 months behind on cyber , Epoch AI, October 16, 2026 (release dates & Cyber ECI scores : Claude Mythos Preview [April 7, 2026, ECI 164.8], Claude Mythos 5 [June 9, 2026, ECI 168.3], Claude Opus 5 [July 24, 2026, ECI 167.5], Zhipu GLM-5.3 [August 14, 2026, ECI 160.1]) ; Artificial Analysis : Claude Opus 5.5 vs GLM-5.3 & Anthropic API Pricing . Calculation : for a 100m-token break-in at the Artificial Analysis 7:2:1 cached-input / uncached-input / output agentic ratio, Claude Mythos 5 ($10/$50/$1 per MTok) = $770 ; Claude Opus 5 ($5/$25/$0.50 per MTok) = $385 ; Zhipu GLM-5.3 ($0.902/MTok blended on Z.ai) = $90.20 (1/55th to 1/111th of BIS’s $5k–$10k April Mythos Preview range). ↩︎ 
 
 
 Alexej Pikovsky, AI SOC Economics : Costs, Pricing Models, & Who Keeps the Savings , July 11, 2026 (updated September 15, 2026), & Edward Wu on Cloud Security Podcast : The Truth About Agentic AI in the SOC , July 29, 2025 (100+ language-model calls per alert investigation, ~20k to 50k tokens or ~$2 of compute per alert). ↩︎ 
 
 
 Vivekananda Allam et al., Tipping the Scales : How AI Shapes the Offense-Defense Balance in Cyberspace , Center for a New American Security, September 23, 2025. ↩︎ 
 
 
 Defending Against AI-Powered Attackers : Office Hours with Sunil Agrawal, CISO at Glean , tomtunguz.com. ↩︎ 
 
 
 CrowdStrike 2026 Global Threat Report, as cited in Cloud Security Alliance, AI-Induced Lateral Movement & Non-Human Identity Risk , March 9, 2026 : average eCrime breakout time of 29 minutes, with a fastest recorded breakout of 27 seconds. ↩︎ 
 
 
 Cloud Security Alliance, Hugging Face Breach : Anatomy of a Rogue AI Agent Swarm (~700 active agents out of ~1,200 exchanging 70,000+ messages across July 9–13, 2026, logging ~17,600 actions & harvesting 136 production secrets), & Cogent Research, Beyond the Human Horizon : Q4 2026 Threat Report (across 50+ Fortune 1000 enterprises, 34 of 45 new monthly crown-jewel attack paths [76%, up 386% year over year] are viable only for parallel AI agent swarms). ↩︎ 
 
 
 Beyond Automation at OpenAI : Office Hours with Arvind KC , tomtunguz.com (span of control shifting from 7 people to 100 to 1,000 agents), & Semperis : Security in the AI Era (Microsoft estimate of 10 non-human identities per human trending toward 100 to 1). ↩︎ 
 
 
 Rubrik Zero Labs & KPMG, Invisible Access, Visible Risk , December 2025 : non-human identities & autonomous agents outnumber human users by 82 to 1 in enterprise environments. ↩︎

</details>