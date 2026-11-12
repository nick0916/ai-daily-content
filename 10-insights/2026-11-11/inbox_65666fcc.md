---
id: inbox_65666fcc
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0253-creator-economy-when-to-use-fable-5-2-vs-opus-5-5-in-cla-0941]]"
title: "When to Use Fable 5.2 vs Opus 5.5 in Claude Code (Full Tutorial)"
url: https://creatoreconomy.so/p/when-to-use-fable-vs-opus-in-claude-code-full-tutorial
source: creator-economy
published_at: 2026-11-11T16:30:08+00:00
fetched_at: 2026-11-12T03:04:04.663759+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Fable 5.2 能力較強但價格為 Opus 5.5 兩倍，建議日常用 Opus、難題才用 Fable。 **Why** Fable 5.2 在多數任務上勝過 Opus 5.5，但每 token 價格與 Max 方案的額度消耗都較高，選模型需要權衡。 **How** 作者在 Claude Code 中用五個實際情境比較兩者，並整理 Anthropic 工程師 Alex 的建議，例如先請 Fable 指出想法的缺陷、用 medium effort、事先說明哪些需要核准。 **What** Fable 在 Max 方案中最多可占每週額度的一半；作者用 Opus 處理信件、自動化流程與個人 app，用 Fable 處理商業策略、照顧母親的長期決策，以及審查 AI skills 的錯誤。"
key_points:
  - "Fable 5.2 每 token 價格為 Opus 5.5 的 2 倍；Max 方案下 Fable 最多可占每週額度的一半"
  - "作者建議 Opus 當日常主力、Fable 用於最難的工作；Alex 建議 Fable 用 medium effort、先請它挑戰想法、預先定義需核准的範圍，並交付整個專案而非單一步驟"
  - "本文為 Anthropic 贊助內容，作者聲明意見獨立；五個情境的完整提示詞需看原文教學"
tags: [claude-code, fable-5-2, opus-5-5, model-selection, sponsored]
topics: [foundation_models.claude, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## When to Use Fable 5.2 vs Opus 5.5 in Claude Code (Full Tutorial)

Fable 5.2 能力較強但價格為 Opus 5.5 兩倍，建議日常用 Opus、難題才用 Fable。

**Why** Fable 5.2 在多數任務上勝過 Opus 5.5，但每 token 價格與 Max 方案的額度消耗都較高，選模型需要權衡。

**How** 作者在 Claude Code 中用五個實際情境比較兩者，並整理 Anthropic 工程師 Alex 的建議，例如先請 Fable 指出想法的缺陷、用 medium effort、事先說明哪些需要核准。

**What** Fable 在 Max 方案中最多可占每週額度的一半；作者用 Opus 處理信件、自動化流程與個人 app，用 Fable 處理商業策略、照顧母親的長期決策，以及審查 AI skills 的錯誤。

### 重點
- Fable 5.2 每 token 價格為 Opus 5.5 的 2 倍；Max 方案下 Fable 最多可占每週額度的一半
- 作者建議 Opus 當日常主力、Fable 用於最難的工作；Alex 建議 Fable 用 medium effort、先請它挑戰想法、預先定義需核准的範圍，並交付整個專案而非單一步驟
- 本文為 Anthropic 贊助內容，作者聲明意見獨立；五個情境的完整提示詞需看原文教學

**原文：** [creator-economy](https://creatoreconomy.so/p/when-to-use-fable-vs-opus-in-claude-code-full-tutorial)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Upgrade to paid to unlock $600+ in AI tool credits, including upcoming Claude Max codes for my paid subscribers only (coming next week!). Get instant access Dear subscribers, With the launch of Fable 5.2, Anthropic now has the two best models in the world (Opus 5.5 is the other one). I've spent 500+ hours using both models in Claude Code. In this video and post, I’ll show you exactly how I use each across 5 real use cases. Watch the tutorial now or read the written guide below. This post is sponsored by Anthropic, but opinions are my own. I cover: (00:00) Fable 5.2 vs Opus 5.5: When to use each model (02:32) My Claude Code setup revealed (03:30) Set up a chief of staff for your inbox and calendar (Opus) (06:11) Create an advisor for your career and life (Fable) (09:14) Automate a complete workflow end-to-end (Opus) (14:01) Design and build a mobile app with Claude Design (Opus) (18:47) Help a loved one through a long-term illness (Fable) (20:54) The secret prompt that improves your AI skills over time I’m proud to partner with Riverside Riverside just launched four AI agents to help you create videos end to end. You can direct them to prep your recording, edit the episode, cut clips, and handle publishing to social, all in one place. Each agent specializes in one job, and the team learns how you like things done and only gets better over time. Try all four agents now and use my exclusive code PETERYANG to get one month free. Get 1 Month Free When to use Fable 5.2 vs Opus 5.5 Here’s the TL;DR from Anthropic’s Fable 5.2 post : Fable is smarter than Opus on most tasks, including coding, long-running agents, and more. I used it to build a 3D kart racer you can play for free. Fable costs 2x as much per token as Opus. On the Max plan, you can use Fable for up to half of your weekly limit. Even though Fable is better, I don’t recommend using it for everything because Opus 5.5 is still an incredible model. Instead, my advice is to: Use Opus as your daily driver and Fable for your hardest work. Alex (AI researcher) at Anthropic shared some great tips for using Fable: Ask Fable what’s wrong with your idea before it builds anything. Use Fable on medium effort , which is what Anthropic employees do too. Tell Fable upfront what needs your approval and what it can do on its own. Give it a whole project instead of a single next step , because Fable can think through the steps on its own. Personally, I use Opus for managing my emails, automating workflows, and building personal apps. I use Fable for getting strategic advice on my business, caring for my mom, and auditing all my AI skills for bugs or issues. In the rest of this post, I’ll walk through each use case with exact prompts you can copy to set them up yourself: 1. Set up a chief of staff for your inbox and calendar 
 
 
 Read more

</details>