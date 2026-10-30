---
id: inbox_9f0db8ab
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/0035-github-trending-agent-tools-donchitos-claude-code-game-studios-29-17-902e]]"
title: "Donchitos/Claude-Code-Game-Studios ⭐ 29,175(今日 +353)"
url: https://github.com/Donchitos/Claude-Code-Game-Studios
source: github-trending-agent-tools
published_at: 2026-10-30T00:35:44.429592+00:00
fetched_at: 2026-10-30T00:44:19.937826+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 49 個 AI agent 與 74 個 skill，把 Claude Code 組織成遊戲工作室式的團隊架構。 **Why** 單一 chat session 缺乏結構，容易跳過設計文件與品質把關。 **How** 依工作室階層（導演、部門主管、專員）分層，並提供 /start、/sprint-plan 等指令與品質閘門，可依 rigor 等級（minimal、standard、full）切換流程強度。 **What** 作者實測四款遊戲，較重流程的 standard 版本多產出 29 份文件，但盲評與實機試玩排名最後；作者因此將預設設為 minimal。"
key_points:
  - "modes.rigor 一次切換六項設定：GDD 必要段落、文件密度、QA 等級、故事粒度、審查模式與團隊規模。"
  - "實測結果：standard 比 minimal 多 29 份文件，盲評與實機試玩排名最後，作者認為文件換來的是可追溯性，而非更好的遊戲。"
  - "規則：改動玩家畫面的 story 須實際啟動遊戲、觀察並把截圖存到 production/qa/evidence/，解析通過不算驗證。"
tags: [claude-code, multi-agent, game-dev, process-overhead, agent-orchestration]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Donchitos/Claude-Code-Game-Studios ⭐ 29,175(今日 +353)

用 49 個 AI agent 與 74 個 skill，把 Claude Code 組織成遊戲工作室式的團隊架構。

**Why** 單一 chat session 缺乏結構，容易跳過設計文件與品質把關。

**How** 依工作室階層（導演、部門主管、專員）分層，並提供 /start、/sprint-plan 等指令與品質閘門，可依 rigor 等級（minimal、standard、full）切換流程強度。

**What** 作者實測四款遊戲，較重流程的 standard 版本多產出 29 份文件，但盲評與實機試玩排名最後；作者因此將預設設為 minimal。

### 重點
- modes.rigor 一次切換六項設定：GDD 必要段落、文件密度、QA 等級、故事粒度、審查模式與團隊規模。
- 實測結果：standard 比 minimal 多 29 份文件，盲評與實機試玩排名最後，作者認為文件換來的是可追溯性，而非更好的遊戲。
- 規則：改動玩家畫面的 story 須實際啟動遊戲、觀察並把截圖存到 production/qa/evidence/，解析通過不算驗證。

**原文：** [github-trending-agent-tools](https://github.com/Donchitos/Claude-Code-Game-Studios)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Turn Claude Code into a full game dev studio — 49 AI agents, 72 workflow skills, and a complete coordination system mirroring real studio hierarchy.

Claude Code Game Studios

Why This Exists

Table of Contents

What's Included

Studio Hierarchy

Slash Commands

Does it produce games, or documents?

Getting Started

Configuration

Upgrading

Project Structure

How It Works

Design Philosophy

Customization

Platform Support

Community

Supporting This Project

License

Engine Specialists

It runs the game and looks at it

Prerequisites

Setup

Testing your customizations

Agent Coordination

Collaborative, Not Autonomous

Automated Safety

Path-Scoped Rules

Turn a single Claude Code session into a full game development studio. 49 agents. 74 skills. One coordinated AI team.

 

Building a game solo with AI is powerful — but a single chat session has no structure. No one stops you from hardcoding magic numbers, skipping design docs, or writing spaghetti code. There's no QA pass, no design review, no one asking "does this actually fit the game's vision?"

Claude Code Game Studios solves this by giving your AI session the structure of a real studio. Instead of one general-purpose assistant, you get 49 specialized agents organized into a studio hierarchy — directors who guard the vision, department leads who own their domains, and specialists who do the hands-on work. Each agent has defined responsibilities, escalation paths, and quality gates.

The result: you still make every decision, but now you have a team that asks the right questions, catches mistakes early, and keeps your project organized from first brainstorm to launch.

Agents are organized into three tiers, matching how real studios operate:

Each agent declares a model in its frontmatter: the three directors ask for
Opus, lead-programmer and fifteen specialists name Sonnet, and the remaining thirty inherit your session's model . Treat the tiers as seniority of role, not as
a billing plan — most of the studio runs on whatever model you are already using.

The template includes agent sets for all three major engines. Use the set that matches your project:

Type / in Claude Code to access all 74 skills:

Onboarding & Navigation /start /help /project-stage-detect /setup-engine /adopt /settings

Game Design /brainstorm /map-systems /design-system /quick-design /review-all-gdds /propagate-design-change

Art & Assets /art-bible /asset-spec /asset-audit

UX & Interface Design /ux-design /ux-review

Architecture /create-architecture /architecture-decision /architecture-review /create-control-manifest

Stories & Sprints /create-epics /create-stories /dev-story /sprint-plan /sprint-status /story-readiness /story-done /estimate

Reviews & Analysis /design-review /code-review /balance-check /content-audit /scope-check /perf-profile /tech-debt /gate-check /consistency-check /security-audit

QA & Testing /qa-plan /smoke-check /soak-test /regression-suite /test-setup /test-helpers /test-evidence-review /test-flakiness /skill-test /skill-improve

Production /milestone-review /retrospective /bug-report /bug-triage /reverse-document /playtest-report

Release /release-checklist /launch-checklist /changelog /patch-notes /hotfix /day-one-patch

Creative & Content /prototype /vertical-slice /onboard /localize

Team Orchestration (coordinate multiple agents on a single feature) /team-combat /team-narrative /team-ui /team-release /team-polish /team-audio /team-level /team-live-ops /team-qa

A fair question, and the answer is a measurement rather than a sample project.
Four games were built from one brief at different modes.rigor levels and the
documents each wrote before its first line of game code were counted:

All of them produced a running, tested game. Two blind reviewers and a human
playtest then ranked the standard build last — the extra 29 documents
bought traceability, not a better game.

The measurement above is about cost. The other half is whether the thing works,
and for a game that means someone has to look at it — a passing test says
nothing about a menu drawn off-screen. So a story that changes anything the
player sees is not closed until the game has been launched, observed, and a
screenshot retained in production/qa/evidence/ . A parse check is not a run.
This holds at every rigor level, including minimal , where automated tests are
waived but the look is not.

The games themselves are deliberately not shipped here: this is a template
you clone to start your own project, and somebody else's game in your repo is
clutter, not evidence.

Hooks fail gracefully if optional tools are missing — you just lose validation — with one deliberate exception: a commit that stages data JSON is blocked when there is no Python to validate it.

Clone or use as template :

Open Claude Code in the project's root folder (the one holding CLAUDE.md and project.yaml ) and start a session:

Starting it in a subfolder such as src/ skips the project's hooks, deny
rules and ask-first permission mode.

Run /start — the system asks where you are (no idea, vague concept,
clear design, existing work) and guides you to the right workflow. No assumptions.

Or jump directly to a specific skill if you already know what you need:

project.yaml at the repo root is the single source of truth for how the
studio behaves on your project — engine, naming conventions, and a modes block that controls how much process every skill enforces. /start writes it
for you; you rarely need to hand-edit it.

The one question that matters most is modes.rigor — minimal , standard ,
or full . It's a single front door over six separate knobs ( workflow —
which GDD sections are required, docs.density , qa.level , story_granularity , review_mode — how many director agents review your work,
and team.size ), so /start asks it once instead of six times:

minimal is the default because the heavier tier costs more to reach working
code without producing a better result, and gives nothing back when someone new
picks the project up. Raise it in one /settings call when your

</details>