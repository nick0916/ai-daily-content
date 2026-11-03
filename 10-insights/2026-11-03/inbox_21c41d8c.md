---
id: inbox_21c41d8c
date: 2026-11-03
source_ref: "[[00-inbox/2026-11-03/2348-github-trending-agent-tools-spotify-portal-ai-plugins-3-030-94-46aa]]"
title: "spotify/portal-ai-plugins ⭐ 3,030(今日 +94)"
url: https://github.com/spotify/portal-ai-plugins
source: github-trending-agent-tools
published_at: 2026-11-03T23:48:40.157884+00:00
fetched_at: 2026-11-03T23:57:37.238997+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Spotify 開源的外掛，讓 Claude Code、Codex、Cursor、pi 等 coding agent 直接操作 Portal 的軟體目錄與服務。 **Why** 讓開發者不必離開 coding agent 就能查詢服務擁有者、健康狀態與文件，並執行 Portal 動作。 **How** 外掛透過 Portal CLI 的 actions registry 呼叫上游 CLI，動作內建 help、dry-run 與確認防護；其中 shunt 外掛（目前僅支援 Claude Code）把大量讀檔、樣板生成等 I/O 密集工作轉交給較便宜的 worker model（AiKA modes）以節省 token。 **What** 倉庫提供 setup、diagnostics、catalog search、service briefing、actions 與 Fleetshift shift 等 workflow，GitHub 今日 +94 星、累計約 3,030 星。"
key_points:
  - "同一個 marketplace 支援 Claude Code、Codex、Cursor、pi，安裝指令各不相同（例如 `claude plugin install portal@portal`）。"
  - "shunt 外掛把 I/O 密集工作路由到較便宜的 worker model，README 標示目的為節省 token，目前僅支援 Claude Code。"
  - "Portal 動作呼叫含 dry-run 與確認步驟，降低 agent 誤執行的風險。"
tags: [claude-code, codex, cursor, plugin, developer-tools, cost-optimization]
topics: [agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## spotify/portal-ai-plugins ⭐ 3,030(今日 +94)

Spotify 開源的外掛，讓 Claude Code、Codex、Cursor、pi 等 coding agent 直接操作 Portal 的軟體目錄與服務。

**Why** 讓開發者不必離開 coding agent 就能查詢服務擁有者、健康狀態與文件，並執行 Portal 動作。

**How** 外掛透過 Portal CLI 的 actions registry 呼叫上游 CLI，動作內建 help、dry-run 與確認防護；其中 shunt 外掛（目前僅支援 Claude Code）把大量讀檔、樣板生成等 I/O 密集工作轉交給較便宜的 worker model（AiKA modes）以節省 token。

**What** 倉庫提供 setup、diagnostics、catalog search、service briefing、actions 與 Fleetshift shift 等 workflow，GitHub 今日 +94 星、累計約 3,030 星。

### 重點
- 同一個 marketplace 支援 Claude Code、Codex、Cursor、pi，安裝指令各不相同（例如 `claude plugin install portal@portal`）。
- shunt 外掛把 I/O 密集工作路由到較便宜的 worker model，README 標示目的為節省 token，目前僅支援 Claude Code。
- Portal 動作呼叫含 dry-run 與確認步驟，降低 agent 誤執行的風險。

**原文：** [github-trending-agent-tools](https://github.com/spotify/portal-ai-plugins)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Spotify Portal AI Plugins

Highlights

Installation

Workflows

Portal CLI

Claude Code

Codex

Cursor

pi

Bring Spotify Portal into Claude Code, Codex, Cursor, and pi.

This plugin provides focused workflows for the Portal CLI : set up
authentication, search your software catalog, build service briefings, run
diagnostics, and invoke Portal actions.

The marketplace also ships shunt (Claude Code only for now): a plugin that routes I/O-heavy agent work — bulk file reads and boilerplate generation — to AiKA modes running cheaper worker models, via the Portal CLI actions registry. See plugins/shunt/README.md .

Start a new session and run:

Open /plugins , install Spotify Portal, start a new task, and ask:

Register the spotify/portal-ai-plugins repository in your Cursor team marketplace, then install Spotify Portal from Cursor Settings → Plugins .

Start a new session and run:

The workflows invoke the upstream CLI through:

Setup verifies the required auth , actions , owner , search , and service commands before proceeding.

Set up the Portal CLI for your current coding-agent environment.

Run read-only diagnostics to verify plugin, CLI, authentication, and action readiness.

Search the software catalog and technical documentation using natural language queries.

Generate concise service briefings with available ownership, health, incident, and documentation details.

Discover and safely invoke Portal actions with built-in help, dry-run, and confirmation safeguards.

Create, run, check, and troubleshoot Fleetshift shifts, open PRs from completed runs, and stop a run on request.

claude plugin marketplace add spotify/portal-ai-plugins
claude plugin install portal@portal
claude plugin install shunt@portal # optional: token-saving AiKA delegation

/portal:setup

codex plugin marketplace add spotify/portal-ai-plugins
codex

Set up Spotify Portal for me.

pi install git:github.com/spotify/portal-ai-plugins

/skill:setup

npx @spotify/portal-cli

</details>