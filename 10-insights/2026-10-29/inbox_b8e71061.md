---
id: inbox_b8e71061
date: 2026-10-29
source_ref: "[[00-inbox/2026-10-29/0034-simon-willison-building-a-multiplayer-game-world-with-a-9173]]"
title: "Building a multiplayer game world with autonomous Fable-class models"
url: https://simonwillison.net/2026/Oct/29/how-i-built-the-most-ai-pilled-company-in-the-world/
source: simon-willison
published_at: 2026-10-29T17:00:26+00:00
fetched_at: 2026-10-30T00:39:08.923343+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一家遊戲公司讓一群 AI agent 自己改程式、每小時上線，連 bug 回報都由 AI 處理。 **Why** 回饋迴圈越短，agent 越不會因為上下文太久遠而失去一致性，所以他們把部署頻率拉到極限。 **How** Agent 直接修改線上程式碼、每小時上線，並讀取錯誤、bug 回報與指標；出問題時可在 30 秒內精準回滾，警報會喚醒負責該事件的 agent，且團隊會刻意製造故障測試恢復路徑。 **What** Jacob Sansbury 描述 Spawn（多人遊戲，玩家用 prompt 讓 AI 角色 Savi 修改遊戲世界）由 Fable 驅動的 agent swarm 自主開發，每月 token 成本逾 $300 萬（稱為 30 倍薪資）。約 60% 的工作源自 production 錯誤、Savi bug 回報、異常 log 或功能請求，一小時沒上線就視為 SEV-0。據作者說法，Fable 5 / 5.1 才讓此自主程度可行，Opus 5.5 不夠用，GPT-6 Astra 做資安修復時把有風險的功能全部關掉；Simon Willison 認為高風險軟體難以採用此作法。"
key_points:
  - "Spawn 由 Fable 驅動的 agent swarm 自主開發，token 成本逾 $300 萬/月，每小時上線；一小時沒出貨視為 SEV-0"
  - "約 60% 工作源自 production 錯誤、Savi bug 回報、log 異常或功能請求；30 秒精準回滾並刻意製造故障測試恢復路徑"
  - "模型差異：作者稱 Fable 5/5.1 才做得到，Opus 5.5 不夠，GPT-6 Astra 修資安時把功能全部關閉"
tags: [agentic-engineering, continuous-deployment, coding-agents, fable, spawn]
topics: [agents.coding_agents, foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Building a multiplayer game world with autonomous Fable-class models

一家遊戲公司讓一群 AI agent 自己改程式、每小時上線，連 bug 回報都由 AI 處理。

**Why** 回饋迴圈越短，agent 越不會因為上下文太久遠而失去一致性，所以他們把部署頻率拉到極限。

**How** Agent 直接修改線上程式碼、每小時上線，並讀取錯誤、bug 回報與指標；出問題時可在 30 秒內精準回滾，警報會喚醒負責該事件的 agent，且團隊會刻意製造故障測試恢復路徑。

**What** Jacob Sansbury 描述 Spawn（多人遊戲，玩家用 prompt 讓 AI 角色 Savi 修改遊戲世界）由 Fable 驅動的 agent swarm 自主開發，每月 token 成本逾 $300 萬（稱為 30 倍薪資）。約 60% 的工作源自 production 錯誤、Savi bug 回報、異常 log 或功能請求，一小時沒上線就視為 SEV-0。據作者說法，Fable 5 / 5.1 才讓此自主程度可行，Opus 5.5 不夠用，GPT-6 Astra 做資安修復時把有風險的功能全部關掉；Simon Willison 認為高風險軟體難以採用此作法。

### 重點
- Spawn 由 Fable 驅動的 agent swarm 自主開發，token 成本逾 $300 萬/月，每小時上線；一小時沒出貨視為 SEV-0
- 約 60% 工作源自 production 錯誤、Savi bug 回報、log 異常或功能請求；30 秒精準回滾並刻意製造故障測試恢復路徑
- 模型差異：作者稱 Fable 5/5.1 才做得到，Opus 5.5 不夠，GPT-6 Astra 修資安時把功能全部關閉

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/29/how-i-built-the-most-ai-pilled-company-in-the-world/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How I Built the Most AI-Pilled Company in the World 
Don't be put off by the clickbait headline, this piece by Jacob Sansbury describing how they are building Spawn is a fascinating exploration of the bleeding edge of what's possible with agentic engineering against frontier models. 
 Spawn is a massively multiplayer gaming environment where players can use prompts (to the in-game agent, Savi) to modify the game world. 
 I fired it up on my phone for a few minutes and was able to prompt a castle into existence, then a dragon, then ride the dragon to fly around that castle. 
 
 By Jacob's telling, Spawn is now being developed autonomously by a swarm of Fable-powered agents costing over $3 million in tokens per month ("we spend 30x payroll on AI tokens"). 
 
 Our agents change the live code directly and ship to production hourly, so they read every error, bug report and metric themselves. About 60% of our work starts from a production error, a Savi bug report (Savi is the AI you build games with in Spawn), something odd in our logs, or a feature request. 
 Savi files bugs herself. When a user hits one, or Savi hits one in the product, she files it. It goes straight to an agent that decides whether it's a real bug to fix, something we won't fix, or intentional design that needs a decision. Usually it becomes a change, delivered to that user within an hour, with a message in the same chat. 
 
 This is continuous deployment turned up to 11: 
 
 A loop this tight only works if it never stops, so we treat an hour without a ship as a SEV-0, our most severe kind of incident. Unshipped changes pile up, and every problem already in production lasts longer. The feedback slows down too. An agent can only keep a few hours of work in its head, so shipping faster than that actually helps it stay coherent. [...] 
 We can roll back a broken change in 30 seconds, exactly where it's broken and nowhere else. When a monitor or a log alert fires, it starts or wakes an agent that owns the incident, and we break things on purpose to test that those recovery paths work. 
 
 My eyebrows raised at least a dozen times reading this. I have trouble imagining this style of development working on software with higher stakes for when something goes wrong, but for a game this appears to be working surprisingly well. 
 Jacob says that Fable 5 (and then 5.1) was the model that made this level of autonomy possible. Opus 5.5 doesn't quite hack it for them, and when they tried GPT-6 Astra to apply fixes from a security review everything stopped working: 
 
 Every feature had been disabled and marked to be turned on again once the security fixes were done. Astra had gone through our whole product and made the insecure things secure by turning them off. 
 
 These kinds of extreme experiments are why I'm excited about game development as a substrate for exploring the edges of what today's coding agents can do.

 Tags: game-design , ai , generative-ai , llms , claude , coding-agents , agentic-engineering , claude-mythos-fable

</details>