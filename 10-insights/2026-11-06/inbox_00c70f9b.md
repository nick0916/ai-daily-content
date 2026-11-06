---
id: inbox_00c70f9b
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0003-github-trending-agent-tools-garrytan-gstack-139-928-612-aff8]]"
title: "garrytan/gstack ⭐ 139,928(今日 +612)"
url: https://github.com/garrytan/gstack
source: github-trending-agent-tools
published_at: 2026-11-06T00:03:12.009832+00:00
fetched_at: 2026-11-06T00:14:24.032778+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 Claude Code 變成一支由 23 個角色化指令組成的虛擬工程團隊，依衝刺流程串接。 **Why** 作者表示這是自己每天使用的開源工作流，希望讓所有人都能取得。 **How** 以 Markdown slash commands 扮演 CEO、設計師、工程經理、QA、資安與發版工程師等角色，依 Think→Plan→Build→Review→Test→Ship→Reflect 順序運作。 **What** 倉庫為 MIT 授權，需 Claude Code、Git 與 Bun v1.4.2 以上；/autoplan 可端到端審查計畫，/ship 會執行測試、審查並開 PR，/cso 做 OWASP + STRIDE 審計。"
key_points:
  - "安裝方式為 git clone 至 ~/.claude/skills/gstack 後執行 ./setup；團隊模式可在共用倉庫自動更新，預設跟隨每週兩次的穩定 release。"
  - "各指令銜接：/office-hours 產出的設計文件由 /plan-ceo-review 讀取，/plan-eng-review 的測試計畫由 /qa 接手，/review 找出的 bug 由 /ship 驗證修正。"
  - "除 Claude Code 外，可用 --host 安裝至其他 agent；macOS 15+ 建議搭配 Aside 瀏覽器，並內建 GBrain 作為跨 session 的持久知識庫。"
tags: [claude-code, agent-skills, sprint-workflow, multi-agent-roles, open-source]
topics: [agents.coding_agents, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## garrytan/gstack ⭐ 139,928(今日 +612)

把 Claude Code 變成一支由 23 個角色化指令組成的虛擬工程團隊，依衝刺流程串接。

**Why** 作者表示這是自己每天使用的開源工作流，希望讓所有人都能取得。

**How** 以 Markdown slash commands 扮演 CEO、設計師、工程經理、QA、資安與發版工程師等角色，依 Think→Plan→Build→Review→Test→Ship→Reflect 順序運作。

**What** 倉庫為 MIT 授權，需 Claude Code、Git 與 Bun v1.4.2 以上；/autoplan 可端到端審查計畫，/ship 會執行測試、審查並開 PR，/cso 做 OWASP + STRIDE 審計。

### 重點
- 安裝方式為 git clone 至 ~/.claude/skills/gstack 後執行 ./setup；團隊模式可在共用倉庫自動更新，預設跟隨每週兩次的穩定 release。
- 各指令銜接：/office-hours 產出的設計文件由 /plan-ceo-review 讀取，/plan-eng-review 的測試計畫由 /qa 接手，/review 找出的 bug 由 /ship 驗證修正。
- 除 Claude Code 外，可用 --host 安裝至其他 agent；macOS 15+ 建議搭配 Aside 瀏覽器，並內建 GBrain 作為跨 session 的持久知識庫。

**原文：** [github-trending-agent-tools](https://github.com/garrytan/gstack)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Use Garry Tan's exact Claude Code setup: 23 opinionated tools that serve as CEO, Designer, Eng Manager, Release Manager, Doc Engineer, and QA

gstack

Quick start

Install — about 30 seconds

See it work

The sprint

GBrain — persistent knowledge for your coding agent

Platform notes

Docs

Privacy & Telemetry

Troubleshooting

License

Step 1: Install on your machine

Step 2: Team mode — auto-update for shared repos (recommended)

Other AI Agents

Which review should I use?

Power tools

gstack turns Claude Code (and other coding agents) into a virtual engineering team: a CEO who rethinks the product, an eng manager who locks architecture, a designer who catches AI slop, a reviewer who finds production bugs, a QA lead who opens a real browser, a security officer who runs OWASP + STRIDE audits, and a release engineer who ships the PR. All slash commands, all Markdown, all free, MIT license.

I'm Garry Tan , President & CEO of Y Combinator . This is the open source software factory I use every day, and I'm sharing it because these tools should be available to everyone. The story, the productivity numbers and how I run ten sprints at once are in Why gstack .

Fork it. Improve it. Make it yours. And if you want to hate on free open source software — you're welcome to, but I'd rather you just try it first.

Who this is for:

Stop there. You'll know if this is for you. When you want the whole sprint, /autoplan reviews a plan end to end and /ship runs tests, review and the PR.

Requirements: Claude Code , Git , Bun v1.4.2+ (the tested version; setup refuses Bun older than 1.3.3, which would let compiled tools read a project's .env ), and Node.js on Windows. Recommended on macOS: the Aside browser (macOS 15+), which the browser skills, /make-pdf and /diagram drive first with your real logged-in sessions; without it, ./setup builds gstack's own bundled browser. /cso needs a native toolchain as well; setup says so and leaves it unavailable when the toolchain is absent. Timing, the /cso prerequisites and the hooks setup registers: docs/install.md .

Open Claude Code and paste this. Claude does the rest.

Install gstack: run git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup then add a "gstack" section to CLAUDE.md that says to use the /browse skill from gstack for all web browsing and never use mcp__claude-in-chrome__* tools. Claude Code lists the installed skills itself, so the section needs no skill list. Then ask the user if they also want to add gstack to the current project so teammates get it.

From inside your repo, paste this. Switches you to team mode, bootstraps the repo so teammates get gstack automatically, and commits the change:

No vendored files in your repo, no version drift, no manual upgrades. Every Claude Code session starts with a fast auto-update check (throttled to once/hour, network-failure-safe, completely silent). Team mode follows the stable channel: the twice-weekly tagged release (Monday and Thursday, at most once every 72 hours, plus verified security and regression fixes), not every merge to main. gstack-config set update_channel main follows every merge instead; see docs/releases.md .

Swap required for optional if you'd rather nudge teammates than block them.

Team mode's required hook runs on Node.js, so every teammate needs Node.js on PATH ( details ). To remove gstack later: docs/uninstall.md .

gstack runs on more agents than Claude. Bare ./setup installs for Claude
Code only (run inside OpenClaw, Hermes or a Dot, it also registers gstack's
skills with that harness: docs/hosts.md ).
Pick another agent with --host , or install for every agent setup
detects on this machine with --host auto :

An explicit --host X installs for X only and never changes another agent's
install. /gstack-upgrade refreshes every install it registered, one row per
host, and says which ones failed.

Tiers: full is certified by a real workflow run (see Certify your host ); experimental installs and passes the conformance tests but has no certification run yet; instruction-only installs nothing: setup prints what to copy.

Per-host notes (agent harnesses, Copilot, Antigravity, Gemini CLI, OpenClaw and ClawHub, the Codex behavioral profile and model tiers, outside-review providers, the design binary's models) are in docs/hosts.md . Any rules-reading agent (Zed, Amp, Jules) can use the 2KB agents digest with no install. Adding a host: docs/ADDING_A_HOST.md .

You said "daily briefing app." The agent said "you're building a chief of staff AI" — because it listened to your pain, not your feature request. Eight commands, end to end. That is not a copilot. That is a team.

gstack is a process, not a collection of tools. The skills run in the order a sprint runs:

Think → Plan → Build → Review → Test → Ship → Reflect

Each skill feeds into the next. /office-hours writes a design doc that /plan-ceo-review reads. /plan-eng-review writes a test plan that /qa picks up. /review catches bugs that /ship verifies are fixed. Nothing falls through the cracks because every step knows what came before it.

The same /qa and /qa-only commands test CLIs, APIs, jobs, workers and webhooks with no browser: QA without a webpage .

Beyond the slash commands, gstack ships standalone CLIs ( gstack-egress , gstack-context-bill , gstack-model-benchmark , gstack-pr-wait , the review and evidence ledgers, the iOS QA daemon): docs/standalone-binaries.md . The fallback browser's per-site domain skills and raw CDP escape hatch, and the voice-input aliases many skills carry, have their own pages.

Deep dives with examples and philosophy for every skill →

GBrain is a persistent knowledge base for AI agents — think of it as the memory your agent actually keeps between sessions. GStack gives you a one-command path from zero to "it's running, my agent can call it."

The four setup paths, the per-repo trust policy and memory sync, in brief: docs/gbrain-quick-tour.md . Full monty — every scenario, every flag, every bin helper, every troubleshooting step: USING_GBRAIN_WITH_GS

</details>