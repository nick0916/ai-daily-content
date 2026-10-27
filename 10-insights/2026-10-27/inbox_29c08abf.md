---
id: inbox_29c08abf
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/2338-github-trending-agent-tools-obra-superpowers-306-404-608-8272]]"
title: "obra/superpowers ⭐ 306,404(今日 +608)"
url: https://github.com/obra/superpowers
source: github-trending-agent-tools
published_at: 2026-10-27T23:38:40.836858+00:00
fetched_at: 2026-10-27T23:51:31.213044+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓編碼 agent 先釐清需求、寫計畫，再逐項派子 agent 實作的可組合技能框架。 **Why** 框架設計為讓 agent 看到需求時先停下來問清楚目標，而不是直接寫程式。 **How** 以一組自動觸發的 skills 串起流程：brainstorming 先確認設計、writing-plans 把工作拆成 2–5 分鐘的任務，再由 subagent-driven-development 逐項執行與審查；計畫強調 red/green TDD、YAGNI、DRY。 **What** 支援 Claude Code、Codex CLI、Cursor、Gemini CLI、OpenCode、Pi 等多種 harness，各平台需分別安裝；GitHub 星數 306,404（今日 +608）。"
key_points:
  - "流程：brainstorming 確認設計 → writing-plans 拆成 2–5 分鐘任務 → subagent-driven-development 逐項實作"
  - "計畫要求每個任務有明確檔案路徑與完整程式碼，並強調 red/green TDD、YAGNI、DRY"
  - "支援十多種 harness（Claude Code、Codex CLI、Cursor、Gemini CLI 等），每個平台需分別安裝"
tags: [agent-skills, claude-code, tdd, subagents, software-methodology]
topics: [agents.coding_agents, agents.frameworks]
importance: 3
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## obra/superpowers ⭐ 306,404(今日 +608)

讓編碼 agent 先釐清需求、寫計畫，再逐項派子 agent 實作的可組合技能框架。

**Why** 框架設計為讓 agent 看到需求時先停下來問清楚目標，而不是直接寫程式。

**How** 以一組自動觸發的 skills 串起流程：brainstorming 先確認設計、writing-plans 把工作拆成 2–5 分鐘的任務，再由 subagent-driven-development 逐項執行與審查；計畫強調 red/green TDD、YAGNI、DRY。

**What** 支援 Claude Code、Codex CLI、Cursor、Gemini CLI、OpenCode、Pi 等多種 harness，各平台需分別安裝；GitHub 星數 306,404（今日 +608）。

### 重點
- 流程：brainstorming 確認設計 → writing-plans 拆成 2–5 分鐘任務 → subagent-driven-development 逐項實作
- 計畫要求每個任務有明確檔案路徑與完整程式碼，並強調 red/green TDD、YAGNI、DRY
- 支援十多種 harness（Claude Code、Codex CLI、Cursor、Gemini CLI 等），每個平台需分別安裝

**原文：** [github-trending-agent-tools](https://github.com/obra/superpowers)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

An agentic skills framework & software development methodology that works.

Superpowers

Table of Contents

How it works

Commercial Services

Installation

The Basic Workflow

When Something Goes Wrong

Community

What's Inside

Philosophy

Contributing

Updating

License

Visual companion telemetry

Claude Code

Antigravity

Codex App

Codex CLI

Cursor

Devin CLI

Factory Droid

Gemini CLI

GitHub Copilot CLI

Grok Build CLI

Kimi Code

OpenCode

Pi

Qwen Code

Hermes Agent

Muse

Skills Library

Superpowers is a complete software development methodology for your coding agents, built on top of a set of composable skills and some initial instructions that make sure your agent uses them.

It starts from the moment you fire up your coding agent. As soon as it sees that you're building something, it doesn't just jump into trying to write code. Instead, it steps back and asks you what you're really trying to do.

Once it's teased a spec out of the conversation, it shows it to you in chunks short enough to actually read and digest.

After you've signed off on the design, your agent puts together an implementation plan that's clear enough for an enthusiastic junior engineer with poor taste, no judgement, no project context, and an aversion to testing to follow. It emphasizes true red/green TDD, YAGNI (You Aren't Gonna Need It), and DRY.

Next up, once you say "go", it launches a subagent-driven-development process, having agents work through each engineering task, inspecting and reviewing their work, and continuing forward. It's not uncommon for your agent to work autonomously for a couple hours at a time without deviating from the plan you put together.

There's a bunch more to it, but that's the core of the system. And because the skills trigger automatically, you don't need to do anything special. Your coding agent just has Superpowers.

If you're using Superpowers in enterprise and could benefit from commercial support, additional tooling, or managed spending, please don't hesitate to drop us a line at sales@primeradiant.com .

Installation differs by harness. If you use more than one, install Superpowers separately for each one.

Superpowers is available via the official Claude plugin marketplace

Install the plugin from Anthropic's official marketplace:

The Superpowers marketplace provides Superpowers and some other related plugins for Claude Code.

Register the marketplace:

Install the plugin from this marketplace:

Install Superpowers as a plugin from this repository:

Antigravity lists each installed skill's description, and the description of
the using-superpowers skill prompts the model to load that skill at the start
of a conversation. Reinstall with the same command to update.

Superpowers is available via the official Codex plugin marketplace .

Superpowers is available via the official Codex plugin marketplace .

Open the plugin search interface:

Search for Superpowers:

Select Install Plugin .

In Cursor Agent chat, install from marketplace:

Or search for "superpowers" in the plugin marketplace.

Install the plugin from this repository:

Update to the latest version with:

Register the marketplace:

Install the plugin:

Install the extension:

Update later:

Register the marketplace:

Install the plugin:

Superpowers is available via the official Grok plugin marketplace .

Install the plugin from xAI's official marketplace:

Or open the marketplace in the TUI, search for Superpowers, and install it:

Superpowers is available in Kimi Code's plugin marketplace.

Open Kimi Code's plugin manager:

Go to Marketplace > Superpowers and install it.

Or install directly from this repository:

Detailed docs: docs/README.kimi.md

OpenCode uses its own plugin install; install Superpowers separately even if you
already use it in another harness.

Tell OpenCode:

Detailed docs: docs/README.opencode.md

Install Superpowers as a Pi package from this repository:

For local development, run Pi with this checkout loaded as a temporary package:

The Pi package loads the Superpowers skills and a small extension that injects the using-superpowers bootstrap at session startup and again after compaction. Pi has native skills, so no compatibility Skill tool is required. Subagent and task-list tools remain optional Pi companion packages.

Qwen Code installs plugins from Claude Code marketplaces directly.

Install the plugin from this repository, and pick superpowers when prompted:

Update later:

Install Superpowers as a Hermes plugin from this repository:

Restart any active Hermes sessions after installing. Note: Hermes has no
post-compaction hook, so a very long session that compacts over its first
turn loses the bootstrap — start a fresh session if skills stop triggering.

Superpowers is available as a native Muse plugin — same repo, same skills, all harnesses. The using-superpowers bootstrap is injected via the native SessionStart hook alongside Claude Code, Codex, Cursor, Gemini, Pi, and the rest — no per-session opt-in.

Install from a local checkout:

Or clone and install:

Update later:

Restart any active Muse sessions after installing so the SessionStart hook takes effect — skills are active immediately, hooks require approval on first install. To verify, start a fresh session and send Let's make a react todo list — a working install auto-triggers brainstorming before any code is written. Version is tracked in .version-bump.json so scripts/bump-version.sh keeps it in sync.

brainstorming - Activates before building anything. Draws out what you actually want, and why, through questions that get you describing it, then plays its understanding back for correction. Small changes get agreed in chat; projects get a written design document a builder could plan from.

using-git-worktrees - Activates after design approval. Creates isolated workspace on new branch, runs project setup, verifies clean test baseline.

writing-plans - Activates with approved design. Breaks work into bite-sized tasks (2-5 minutes each). Every task has exact file paths, complete code, verifica

</details>