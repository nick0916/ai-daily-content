---
id: inbox_1b4caec3
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0147-github-trending-agent-tools-tradermonty-claude-trading-skills-4-191-91c8]]"
title: "tradermonty/claude-trading-skills ⭐ 4,191(今日 +69)"
url: https://github.com/tradermonty/claude-trading-skills
source: github-trending-agent-tools
published_at: 2026-11-14T01:47:24.130076+00:00
fetched_at: 2026-11-14T01:57:58.078916+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 Claude Skills 把看盤、選股與交易紀錄流程結構化，而不是讓 AI 直接決定買賣。 **Why** 原文指出目標是讓時間有限的個人投資人改善決策流程，而非外包買賣判斷。 **How** 以 workflows/*.yaml 的機器可讀 manifest 串起多個 skill，明列決策關卡與產出物，可手動執行。 **What** 專案為 MIT 授權，GitHub 星數 4,191（今日 +69）；五個入門 skill 不需付費 API，但作者明言這不是訊號服務，也不保證獲利。"
key_points:
  - "workflows/*.yaml 為正本，列出技能順序、決策關卡與產出物，README 與 CLAUDE.md 若衝突以 skills-index.yaml 為準"
  - "無 FMP、FINVIZ Elite、Alpaca 訂閱時，可用公開 CSV、圖表截圖與本地檔案跑五個入門 skill"
  - "定位為教育與流程改善工具，明確排除全自動交易、訊號外包與短線當沖"
tags: [claude-skills, trading, workflow, investing, decision-process]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## tradermonty/claude-trading-skills ⭐ 4,191(今日 +69)

用 Claude Skills 把看盤、選股與交易紀錄流程結構化，而不是讓 AI 直接決定買賣。

**Why** 原文指出目標是讓時間有限的個人投資人改善決策流程，而非外包買賣判斷。

**How** 以 workflows/*.yaml 的機器可讀 manifest 串起多個 skill，明列決策關卡與產出物，可手動執行。

**What** 專案為 MIT 授權，GitHub 星數 4,191（今日 +69）；五個入門 skill 不需付費 API，但作者明言這不是訊號服務，也不保證獲利。

### 重點
- workflows/*.yaml 為正本，列出技能順序、決策關卡與產出物，README 與 CLAUDE.md 若衝突以 skills-index.yaml 為準
- 無 FMP、FINVIZ Elite、Alpaca 訂閱時，可用公開 CSV、圖表截圖與本地檔案跑五個入門 skill
- 定位為教育與流程改善工具，明確排除全自動交易、訊號外包與短線當沖

**原文：** [github-trending-agent-tools](https://github.com/tradermonty/claude-trading-skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Claude Code skills for equity investors and traders — market analysis, technical charting, economic calendars, screeners, and trading strategy development.

Claude Trading Skills

Disclaimer

Who This Is For

Recommended Starting Path

Repository Layout

Getting Started

Supported platforms

Companion Work Package

Core Skill Areas

Detailed Skill Catalog

Additional Workflow Examples

Contributor Automation

Customization & Contribution

API Requirements

Support & Further Reading

License

See Example Outputs

What This Actually Costs

No API Key Starter Path

Use with Claude Web App

Use with Claude Code (desktop or CLI)

Market Regime

Core Portfolio

Dividend Income

Swing Opportunity

Trade Planning

Trade Memory

Strategy Research

Advanced Satellite

Meta / Development Tooling

Daily Market Monitoring

Weekly Strategy Review

Individual Stock Research

Strategic Positioning

Earnings Momentum Trading

Income Portfolio Construction

Kanchi Dividend Workflow (US Stocks)

Options Strategy Development

Portfolio Review & Rebalancing

Statistical Arbitrage Opportunities

Skill Quality & Automation

Skills Requiring APIs

API Setup

Claude Trading Skills started as a personal project to use AI to improve my own trading process.

Claude Trading Skills is a Claude Skills-based trading workflow toolkit for time-constrained individual investors.

It is designed for investors who use long-term investing, ETFs, and dividend stocks as their core, while using disciplined swing trading as a satellite strategy when market conditions are favorable.

The goal is not to outsource buy/sell decisions to AI. The goal is to structure market review, risk management, trade planning, journaling, and continuous improvement. It is open source because the workflows, checklists, and review habits behind better trading decisions can improve through shared practice.

This is not a signal service or a promise of profitability. It is a toolkit for traders who want to build a better decision process.

The project follows a first for self, open for others stance: it is built first as a practical workflow the author uses, then shared openly for others who face similar constraints.

📖 Documentation site: https://tradermonty.github.io/claude-trading-skills/

Project vision: PROJECT_VISION.md

日本語版READMEは README.ja.md をご覧ください。

This repository is for educational, research, and process-improvement purposes only. It is not financial advice, investment advisory service, tax advice, legal advice, a signal service, or a broker execution platform. Trading and investing involve risk, including loss of principal. Past performance, backtests, screens, reports, and AI-generated analysis do not guarantee future results. All trading decisions, position sizing, tax/regulatory compliance, and broker usage are the user's responsibility.

The project is provided under the MIT License, AS IS, WITHOUT WARRANTY .

This repository is designed for:

It is not designed for fully automated trading, signal outsourcing, or short-term scalping.

New users should start with one of these operational workflows. Each link points to a machine-readable manifest under workflows/ that names the exact skills, decision gates, and artifacts in order.

See workflows/README.md for how to read a manifest and run it manually. For a one-page "which workflow fits my situation?" guide, see Find Your Workflow ( 日本語 ).

New here? Follow Your First Week ( 日本語 ) from installation through a no-paid-data-API market check, first journal entry, and first weekly review.

These visual excerpts use fictional data to show the kinds of results you can review before setting up a skill. They are illustrations, not live market readings or trading instructions.

Select a preview to open the full-size SVG; on a phone, zoom after opening.

Choose a workflow: Trading Skills Navigator recommends a starting path from your goal.

Review market risk: The market-regime-daily workflow ends with an Exposure Coach posture for human review, not an order.

Learn from closed trades: Weekly Performance Digest summarizes realized outcomes and process lessons.

Claude Web Skills are currently available on Free, Pro, Max, Team, and
Enterprise accounts; see Anthropic's current Skills help because access can change. Claude Code has separate account requirements, and
the Claude.ai Free plan does not include it; see the Claude Code setup guide .
FMP, FINVIZ Elite, and Alpaca are optional data or broker integrations for
specific workflows. The five-skill starter path below works with public CSVs,
chart screenshots, and local files, so it does not require a paid market-data
API subscription.

If you do not have FMP / FINVIZ / Alpaca subscriptions, start with these five skills and run them manually:

This path lets you review market conditions, size trades, journal decisions, and review outcomes without paid data APIs . Note: "no API" does not mean "no external data" — these skills still need public CSVs, chart screenshots, or local files. See each skill's integrations: entry in skills-index.yaml for exact input requirements.

Canonical source: skills-index.yaml is the authoritative index of all skills. If this README, CLAUDE.md , or docs disagree with the index, the index is correct. The same applies to multi-skill workflows — workflows/*.yaml is canonical.

First time here? Read the FAQ for plan, cost, safety, and scope
answers.

See the Changelog for changes and the release compatibility and migration policy before updating an installed skill.

Tip: .skill packages are built from the source folders with tests and local build artifacts omitted. Edit a source folder if you want to customize a skill, then run python3 scripts/package_skills.py --skill before uploading to the web app.

The shared project environment supports Python 3.11 to 3.13 on Linux, Windows, and macOS. Packaged standalone skills retain a Python 3.9 source floor. A root-project combination counts as supported only if it is exercised by the project's CI; other combinations in that range are
best-effort and unverified. See docs/dev/compatibility-matrix.md for the exact sup

</details>