---
id: inbox_6dd4675e
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2318-github-trending-agent-tools-mvanhorn-last30days-skill-69-003-772-f690]]"
title: "mvanhorn/last30days-skill ⭐ 69,003(今日 +772)"
url: https://github.com/mvanhorn/last30days-skill
source: github-trending-agent-tools
published_at: 2026-11-17T23:18:24.242549+00:00
fetched_at: 2026-11-17T23:29:56.397013+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI agent 同時搜尋 Reddit、X、YouTube、HN 等社群，依互動量排序後綜整成摘要。 **Why** 單一 AI 無法存取所有平台，一般搜尋偏向編輯內容，不反映社群實際關注的議題。 **How** 以 Agent Skill 並行搜尋多個來源，依 upvotes、likes、Polymarket 市場賠率等互動訊號評分，再由 agent 綜整。 **What** Reddit、HN、Polymarket、GitHub 免設定即可用，設定精靈可解鎖 X、YouTube、TikTok、arXiv、Techmeme 等；支援 Claude Code 與 50 多種 Agent Skills 宿主；今日 GitHub 星數 69,003（+772）。"
key_points:
  - "免設定來源：Reddit、HN、Polymarket、GitHub；需設定才可用：X、YouTube、TikTok、arXiv、Techmeme"
  - "發現模式掃描 Reddit 分類、HN front/best、Digg 等，輸出 5–10 個依動能排序的主題"
  - "每個結果附跨來源數字、動能標籤，以及可直接執行的 /last30days 後續指令"
tags: [research-agent, multi-source-search, social-signals, agent-skill, claude-code]
topics: [agents.frameworks, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## mvanhorn/last30days-skill ⭐ 69,003(今日 +772)

讓 AI agent 同時搜尋 Reddit、X、YouTube、HN 等社群，依互動量排序後綜整成摘要。

**Why** 單一 AI 無法存取所有平台，一般搜尋偏向編輯內容，不反映社群實際關注的議題。

**How** 以 Agent Skill 並行搜尋多個來源，依 upvotes、likes、Polymarket 市場賠率等互動訊號評分，再由 agent 綜整。

**What** Reddit、HN、Polymarket、GitHub 免設定即可用，設定精靈可解鎖 X、YouTube、TikTok、arXiv、Techmeme 等；支援 Claude Code 與 50 多種 Agent Skills 宿主；今日 GitHub 星數 69,003（+772）。

### 重點
- 免設定來源：Reddit、HN、Polymarket、GitHub；需設定才可用：X、YouTube、TikTok、arXiv、Techmeme
- 發現模式掃描 Reddit 分類、HN front/best、Digg 等，輸出 5–10 個依動能排序的主題
- 每個結果附跨來源數字、動能標籤，以及可直接執行的 /last30days 後續指令

**原文：** [github-trending-agent-tools](https://github.com/mvanhorn/last30days-skill)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AI agent skill that researches any topic across Reddit, X, YouTube, HN, Polymarket, and the web - then synthesizes a grounded summary

/last30days

Why this exists

Sources, scored by the people

What people actually use it for

What's new

Install

Bring your own keys

Configuration

Showcase: community research feeds

How it works

What people are saying

Open source

Data handling

Star History

Claude Code (recommended)

Quick Try-Link

Grok (xAI Build CLI)

Codex, Cursor, Copilot, Gemini CLI, and other Agent Skills hosts

claude.ai (web)

Claude Desktop

OpenClaw

Manual (developer)

macOS Keychain (optional)

English | Français | Deutsch | Español | Português (Brasil) | 日本語 | 简体中文 | العربية | فارسی | Türkçe

 

 

An AI agent-led search engine scored by upvotes, likes, and real money - not editors.

This README tracks the current v4 pipeline. The runtime skill spec lives in skills/last30days/SKILL.md , which is the source of truth for the latest command and setup behavior.

Claude Code (recommended — auto-updates via marketplace):

Codex, Cursor, Copilot, Gemini CLI, or any of 50+ Agent Skills hosts:

( -g installs globally for your user, available across all projects. Drop it to scope per-project.)

More install options (claude.ai web, OpenClaw, manual) in the Install section below.

Zero config. Reddit, HN, Polymarket, and GitHub work immediately, and so do patent filings and careers pages when your topic is a company. Run it once and the setup wizard unlocks X, YouTube, TikTok, arXiv, Techmeme, and more in 30 seconds.

Reddit upvotes. X likes. YouTube transcripts. TikTok engagement. Polymarket odds backed by real money and insider information. That's millions of people voting with their attention and their wallets every day. /last30days searches all of it in parallel, scores it by what real people actually engage with, and an AI agent judge synthesizes it into one brief.

Google aggregates editors. /last30days searches people.

You can't get this search anywhere else because no single AI has access to all of it. Google search doesn't touch Reddit comments or X posts. ChatGPT has a deal with Reddit but can't search X or TikTok. Gemini has YouTube but not Reddit. Claude has none of them natively. Each platform is a walled garden with its own API, its own tokens, its own auth. But you can bring your own keys and browser sessions, and suddenly an AI agent can search all of them at once, score them against each other, and tell you what actually matters.

That's the unlock. Not one better search engine. A dozen disconnected platforms, bridged by an agent.

You have a meeting tomorrow. You Google them. You get their LinkedIn from 2023. /last30days gives you what they're actually doing this month: joined OpenAI to work on Codex, fighting Anthropic's ban on third-party agents, shipping 23 PRs at 85% merge rate, building "LobsterOS" for cross-device agent control, and r/ClaudeCode hit 569 upvotes debating whether he's a hero or "insufferable." Scattered across X posts, Reddit threads, YouTube transcripts, and GitHub commits. None of it was on Google.

I built it to keep up in AI. Everything changes every day and the Reddit and X nerds are always on top of it first. I needed better prompts, and the training data was always months behind what the community had already figured out.

But it turned into something bigger. Now I run it before a sales call to know the last 30 days truth about a business. Before a meeting to read someone's recent tweets and podcast transcripts. Before a Disney World trip to know which rides are closed and what the community says about Genie+. Before I build anything to know what problems people are actually hitting.

If you're meeting with a CEO, have you read all their tweets and YouTube transcripts from the last 30 days? I have.

Ask /last30days to include the sources you need. Availability depends on credentials, installed tools, the topic, and explicit opt-ins. See source requirements for configuration.

A Reddit thread with 1,500 upvotes is a stronger signal than a blog post nobody read. A TikTok with 3.6M views tells you more about what's culturally relevant than a press release. Polymarket odds backed by $66K in volume are harder to argue with than a pundit's guess.

The synthesis ranks by what real people actually engaged with. Social relevancy, not SEO relevancy.

Before a meeting. /last30days Peter Steinberger - joined OpenAI's Codex team, fighting Anthropic's ban on third-party agents, 23 PRs merged at 85% merge rate on GitHub, building LobsterOS for cross-device agent control. r/ClaudeCode: "Ever since OpenClaw released, it was widely known that if you run it through anything other than the API, you were gonna get banned eventually" (227 upvotes). That's not on LinkedIn.

To see what a company is building before it ships. /last30days Apple - the Jobs Page Secret Signal flagged a new director role testing whether requests trigger transactions that run through partner APIs and financial systems, which reads like quality control for an assistant that completes purchases. The Patent Secret Signal flagged an application for changing a device's state by tapping it in a saved photo of your room. Polymarket put Apple at 91% to be the world's largest company at year end. /last30days Alphabet found a product manager role for "YouTube Ads Agentic Buyflows", and its stock line read down 17.6% over 30 days while the S&P 500 fell 3.6%, with the worst day on Oct 29 (-12.6%). For a hiring-only report, add --hiring-signals .

To find the topic before it peaks. Ask /last30days what's exploding in AI agents? and the skill switches to discovery mode: the engine sweeps Reddit category listings, Hacker News front/best stories, Digg stories, and X when authenticated; your agent judges the nominations (names, junk filtering, content-worthiness) and writes podcast / X-article angles; then you get 5-10 velocity-ranked topics. Every result includes cross-source numbers, a momentum label, and a ready-to-run /last30days " " follow-up.

When something drops. /last30days Kanye West - UK blocked h

</details>