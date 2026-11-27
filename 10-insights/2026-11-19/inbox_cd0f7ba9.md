---
id: inbox_cd0f7ba9
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0052-latent-space-why-linear-says-issue-tracking-is-dead-c-dd23]]"
title: "Why Linear says Issue Tracking is Dead — Cristina Cordova, COO"
url: https://latent.space/p/why_linear_says_issue_tracking_is_dead_cristina_cordova_coo/
source: latent-space
published_at: 2026-11-19T23:38:57+00:00
fetched_at: 2026-11-27T00:59:03.025792+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Linear 把議題追蹤工具改造成讓 AI agent 自己建立、分派、關閉工作的系統，人只負責看與協調。 **Why** AI 出現後，若 SaaS 只是在資料庫上包一層 MCP server，而 agent 工作流不比產品外部好，就沒人有理由開啟你的 app。 **How** COO 同時盯兩條線：agent 使用量與 app 使用量；agent 升、app 不升代表正在商品化。Linear 在 2025 年 5 月推出 MCP server，並做了 agent 平台、與 Codex、Cursor、GitHub Copilot 整合，以及自家 Linear Agent。 **What** Cristina Cordova 稱 agent 建立的工作從一年前的 3% 升到超過一半；Linear 今年 ARR 破 1 億美元、付費客戶逾 4 萬、淨收入留存率 177%，8 月員工股票出售以 25 億美元估值成交。公司從未聘 SDR、不做 forward deployed engineering，LLM 不單獨回覆客服（AI 起草、人決定），並用「工程/產品/設計/資料至少占 40%」控管人力，約 170 人。"
key_points:
  - "判斷 SaaS 是否被商品化：同時追蹤 agent 使用量與 app 使用量，agent 升而 app 不升就是危險訊號；Linear 兩者都上升"
  - "agent 建立的工作占比從一年前 3% 升到超過 50%；Linear 2025 年 5 月上線 MCP server，並整合 Codex、Cursor、GitHub Copilot"
  - "定價：座位制保留，Linear Agent 對話免費，coding session 依 OpenAI/Anthropic 公開 API 價加小額加成，Loops 用 AI credits；新 AI 功能先免費 beta、價格由高往低調"
tags: [linear, issue-tracking, mcp, agent-orchestration, saas-pricing]
topics: [product_and_org.product, agents.mcp, product_and_org.leadership]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Why Linear says Issue Tracking is Dead — Cristina Cordova, COO

Linear 把議題追蹤工具改造成讓 AI agent 自己建立、分派、關閉工作的系統，人只負責看與協調。

**Why** AI 出現後，若 SaaS 只是在資料庫上包一層 MCP server，而 agent 工作流不比產品外部好，就沒人有理由開啟你的 app。

**How** COO 同時盯兩條線：agent 使用量與 app 使用量；agent 升、app 不升代表正在商品化。Linear 在 2025 年 5 月推出 MCP server，並做了 agent 平台、與 Codex、Cursor、GitHub Copilot 整合，以及自家 Linear Agent。

**What** Cristina Cordova 稱 agent 建立的工作從一年前的 3% 升到超過一半；Linear 今年 ARR 破 1 億美元、付費客戶逾 4 萬、淨收入留存率 177%，8 月員工股票出售以 25 億美元估值成交。公司從未聘 SDR、不做 forward deployed engineering，LLM 不單獨回覆客服（AI 起草、人決定），並用「工程/產品/設計/資料至少占 40%」控管人力，約 170 人。

### 重點
- 判斷 SaaS 是否被商品化：同時追蹤 agent 使用量與 app 使用量，agent 升而 app 不升就是危險訊號；Linear 兩者都上升
- agent 建立的工作占比從一年前 3% 升到超過 50%；Linear 2025 年 5 月上線 MCP server，並整合 Codex、Cursor、GitHub Copilot
- 定價：座位制保留，Linear Agent 對話免費，coding session 依 OpenAI/Anthropic 公開 API 價加小額加成，Loops 用 AI credits；新 AI 功能先免費 beta、價格由高往低調

**原文：** [latent-space](https://latent.space/p/why_linear_says_issue_tracking_is_dead_cristina_cordova_coo/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Linear was founded to build a better issue tracker. Seven years and $134 million in funding later, its CEO Karri Saarinen published a post titled "Issue tracking is dead." In this episode, we chat with Cristina Cordova , COO of Linear , about how the company navigated that and how its go-to-market changed along the way. Cristina spent seven and a half years at Stripe, led platform and partnerships at Notion, and was a partner at First Round before joining Linear in 2023. Linear's founders built it after living with legacy issue trackers at Coinbase, Airbnb and Uber, and it spread self-serve through startups like Vercel and Ramp. When she joined, Linear had about 40 people and one salesperson. Since then it has shipped an MCP server, a platform for building agents into Linear, integrations with Codex, Cursor and GitHub Copilot, and its own Linear Agent. Agents created 3% of Linear's work a year ago. Now it's more than half. Linear passed $100 million in ARR this year with more than 40,000 paying customers and 177% net revenue retention, and in August employees sold $99 million in stock at a $2.5 billion valuation . We talk about why she stopped chasing enterprise deals three weeks after joining, why Linear has never hired a single SDR, why it won't let an LLM answer support tickets on its own, and what the AI budgets behind $100M-in-months ARR mean for everyone else. Half the work on Linear is now created by agents Linear shipped its MCP server in May 2025, and Cristina says it was basically the first in its category. A year and a half later, more than half the issues created in Linear come from agents. That doesn't mean Linear wants to be a database with an MCP server on top. Cristina thinks SaaS companies settling for that are making a big mistake. If the agent workflows inside your product aren't better than the ones outside it, nobody has a reason to open your app. So she watches two lines: agent usage and app usage. If agent usage climbs and app usage doesn't, you're becoming a commodity. At Linear, both are up and to the right, because people still come back to the app to see and coordinate the work. Jump to the MCP discussion → "Issue tracking is dead" When Karri published "Issue tracking is dead" in March, most of Linear's customers agreed with him. Then they asked the obvious question: so what am I buying? Linear's answer is a product development system built around agent orchestration, where humans stop doing the manual work of filing, labeling, assigning and closing issues. Customers had been pushing it there. Most of the frontier AI labs run on Linear and wanted it to move faster. Pre-AI companies like Ramp and Coinbase were building their own internal agents and needed an API to plug them into Linear. Cristina says Linear is lucky it's small enough to cannibalize itself. Google has a much harder problem: put an AI answer above every search result, and fewer people look at the ads. Jump to the "issue tracking is dead" discussion → The AI budget behind $100M in months The thing speeding up purchases right now, Cristina says, is AI budget. Companies carved out money for AI tools that didn't exist before, and any product that fits inside it skips the usual fight for spend. At some companies that budget is very high. It's already starting to change. Buyers are signing one-year deals and paid pilots, not three-year contracts, because nobody knows what they'll want in two years. And some overnight-$100M stories are a handful of $30 to $40 million contracts with defense companies or giant law firms. That's a very different business from Linear's 40,000 paying customers on what was, until June, entirely seat-based pricing. When those one-year deals come up for renewal, we'll find out whose ARR was real. Jump to the AI budget discussion → Linear threw out its 2025 enterprise roadmap Three weeks after joining in 2023, Cristina crossed "move upmarket to enterprise" off Linear's company goals. It had one salesperson. She went after growth-stage companies that would have to rip out an existing tool instead, the same way Stripe won new businesses long before it won switchers. Linear finally declared an enterprise push in 2025, with a roadmap full of features for large organizations. Then agents happened. Linear built an MCP server, an agents platform with a whole new set of APIs, and integrations with Codex, Cursor and GitHub Copilot. None of it was planned, and a lot of the enterprise work never got done. Cristina chose to race ahead anyway. Competitors waited, and enterprises started putting Linear on their shortlists. Jump to the enterprise roadmap discussion → No SDRs, no forward deployed engineers Linear has never hired a single SDR. Cristina thinks the qualification call wastes the customer's time: they want a demo, not questions about their budget. AEs do their own outbound, with tooling to keep it personal. It doesn't do forward deployed engineering either. Linear should be easy enough to adopt that nobody needs access to your systems. Solutions engineers sell alongside enterprise AEs instead, sometimes building a working ServiceNow integration overnight to show a prospect it can be done. Cristina adds that an opinionated tool gives agents cleaner data than one where every team defines "bug" differently. Support stays in-house, and Linear won't let an LLM answer tickets on its own. AI drafts replies and a human decides what goes out. Customers sometimes assume the replies are AI because they arrive so fast. In three and a half years, Cristina has never had an escalation over a bad support experience. Jump to the sales team discussion → Everyone wants outcome-based pricing Cristina would love a model like Intercom's Fin, which charges for each support conversation its AI resolves. It's harder for Linear. What is auto-triaging a bug to the right team worth when one company thinks that's the PM's job and another doesn't? Until someone cracks that, Linear charges for what costs it money and keeps the rest free. Seats stay. Linear Agent chat is free even though it runs on frontier models. In coding sessions, users pick OpenAI or Anthropic models and harnesses, and Linear passes through the published API price plus a small markup. Loops run on AI credits. Linear doesn't start charging for things that used to be free. New AI features launch as free betas with notice that pricing is coming, and prices start high and come down rather than the other way around. Jump to the pricing discussion → Why not hire 100 salespeople? Cristina says Linear runs on about half the headcount of companies at its stage and revenue. A sales team bigger than the rest of the company would have cost it the trust engineering now has in sales. From Stripe she brought a 40% rule: at least 40% of the company should be engineering, product, design and data. If sales wanted more people, it helped recruit engineers first. Linear has no hard rule, but one of the first things she built was a headcount spreadsheet by function, and she still watches the ratio. Hiring is slow on purpose. Candidates do a work trial on a real problem. Hers was writing Linear's go-to-market plan for the next six to twelve months, which then became her job. At about 170 people, the only C-suite is the founders and her. Jump to the hiring discussion → Show notes 
 Linear — the product development system where Cristina is COO. 
 Sharing Linear's growth with the people building it — the August tender at a $2.5 billion valuation, with more than 40,000 paying customers and 177% net revenue retention. 
 Issue tracking is dead — Karri's March post on why Linear is building for agents. 
 Linear MCP server — the May 2025 launch Cristina says was basically a first for the category. 
 Introducing Linear Agent — the built-in agent whose chat Linear keeps free. 
 How we built Triage Intelligence — the feature that suggests labels and catches duplicates in incoming issues, Cristina's example of AI that doesn't need to be an agent 
 Coding sessions in Linear — the June launch that ended Linear's all-seat pricing, running Claude Code and Codex on AI credits. 
 Introducing Loops — recurring agent jobs, also billed with AI credits. 
 Intercom Fin pricing — $0.99 per resolved conversation, the outcome-based model Cristina wishes fit Linear. 
 Timestamps 
 0:00 Intro 
 0:51 Meet Cristina Cordova, COO of Linear 
 1:39 Why Linear hired a COO at 40 people 
 5:01 Her work trial: a go-to-market plan for Linear 
 12:11 Crossing enterprise off the company goals 
 20:00 Why being a database behind an MCP server isn't enough 
 23:39 Selling after "issue tracking is dead" 
 34:40 Smaller, flatter teams and no SDRs 
 36:14 AI-drafted support replies with humans in charge 
 42:23 Why Linear doesn't do forward deployed engineering 
 47:53 Why some AI startups hit $100M ARR so fast 
 50:06 Moving from seats to usage-based pricing 
 57:07 Trading the 2025 enterprise roadmap for agents 
 1:03:28 What Linear's moat is now 
 1:05:54 Why not hire 100 salespeople? 
 1:08:59 Stripe's 40% rule for engineering headcount

</details>