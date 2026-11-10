---
id: inbox_2444e9c2
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2324-github-trending-agent-tools-addyosmani-agent-skills-115-120-465-8a24]]"
title: "addyosmani/agent-skills ⭐ 115,120(今日 +465)"
url: https://github.com/addyosmani/agent-skills
source: github-trending-agent-tools
published_at: 2026-11-10T23:24:05.069505+00:00
fetched_at: 2026-11-10T23:35:06.615107+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把資深工程師的開發流程寫成 Markdown 技能包，讓 AI 寫程式時照著品質關卡走。 **Why** 讓 AI agent 在各開發階段一致地遵循品質關卡，而不是每次臨時提醒。 **How** 25 個 skill（24 個生命週期 skill 加 1 個元技能）各含步驟、驗證關卡與反合理化表格，依定義、規劃、建置、驗證、審查、上線組織。 **What** GitHub 星數 115,120（今日 +465）；提供 9 個對應生命週期的 slash command（文中列出 /spec、/plan、/build、/test、/review、/ship），可透過 open skills CLI 安裝到 70+ 個 agent，或以 Claude Code 外掛、Codex CLI v0.122+ 外掛方式安裝。"
key_points:
  - "25 個 skill（24 個生命週期 skill 加 1 個 using-agent-skills 元技能），每個含步驟、驗證關卡與反合理化表格"
  - "/build 會在一次核准計畫後自動實作所有任務，每個任務仍採測試驅動並個別 commit，遇到失敗或風險步驟會暫停"
  - "安裝方式：open skills CLI 支援 70+ agent；Claude Code 以 plugin 安裝；Codex CLI v0.122+ 以原生 plugin 安裝"
tags: [agent-skills, claude-code, coding-agents, engineering-workflow, open-source]
topics: [agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## addyosmani/agent-skills ⭐ 115,120(今日 +465)

把資深工程師的開發流程寫成 Markdown 技能包，讓 AI 寫程式時照著品質關卡走。

**Why** 讓 AI agent 在各開發階段一致地遵循品質關卡，而不是每次臨時提醒。

**How** 25 個 skill（24 個生命週期 skill 加 1 個元技能）各含步驟、驗證關卡與反合理化表格，依定義、規劃、建置、驗證、審查、上線組織。

**What** GitHub 星數 115,120（今日 +465）；提供 9 個對應生命週期的 slash command（文中列出 /spec、/plan、/build、/test、/review、/ship），可透過 open skills CLI 安裝到 70+ 個 agent，或以 Claude Code 外掛、Codex CLI v0.122+ 外掛方式安裝。

### 重點
- 25 個 skill（24 個生命週期 skill 加 1 個 using-agent-skills 元技能），每個含步驟、驗證關卡與反合理化表格
- /build 會在一次核准計畫後自動實作所有任務，每個任務仍採測試驅動並個別 commit，遇到失敗或風險步驟會暫停
- 安裝方式：open skills CLI 支援 70+ agent；Claude Code 以 plugin 安裝；Codex CLI v0.122+ 以原生 plugin 安裝

**原文：** [github-trending-agent-tools](https://github.com/addyosmani/agent-skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Production-grade engineering skills for AI coding agents.

Agent Skills

Commands

Quick Start

Adoption

All 25 Skills

Agent Personas

Reference Checklists

How Skills Work

Project Structure

Why Agent Skills?

How it compares

Contributing

Team

License

Meta - Discover which skill applies

Define - Clarify what to build

Plan - Break it down

Build - Write the code

Verify - Prove it works

Review - Quality gates before merge

Ship - Deploy with confidence

Production-grade engineering skills for AI coding agents.

Skills encode the workflows, quality gates, and best practices that senior engineers use when building software. These ones are packaged so AI agents follow them consistently across every phase of development.

9 slash commands that map to the development lifecycle. Each one activates the right skills automatically.

In Claude Code these install as plugin commands. Where a built-in command has the same name, as /review does, use the namespaced form: /agent-skills:review .

Want fewer manual steps once the spec exists? /build auto generates the plan and implements every task in a single approved pass — you approve the plan once, then it runs autonomously. It removes the human stepping between tasks, not the verification: every task is still test-driven and committed individually, and it pauses on failures or risky steps.

Skills also activate automatically based on what you're doing — designing an API triggers api-and-interface-design , building UI triggers frontend-ui-engineering , and so on.

Fastest path — any agent, one command. The open skills CLI installs into 70+ agents (Claude Code, Cursor, Codex, Copilot, Cline, and more):

Or grab individual skills:

Installing one skill? A per-skill npx install copies only skills/ / , not the repo-level references/ directory. The skill still
works, but paths to supplementary shared checklists are unavailable. Use a
whole-repo integration, clone the repository, or copy the needed checklist into
a references/ directory inside the installed skill. This portability gap is
tracked in #361 .

Prefer a native integration? Pick your tool below.

Marketplace install:

SSH errors? The marketplace clones repos via SSH. If you don't have SSH keys set up on GitHub, either add your SSH key or use the full HTTPS URL to force HTTPS cloning during the marketplace-add step:

If /plugin install still fails with git@github.com: Permission denied (publickey) on Windows or macOS, the recommended workaround is to configure Git once to rewrite GitHub SSH URLs to HTTPS for subprocess clones:

Local / development:

Put workflow skills under .cursor/skills/ (sync from agent-skills/skills/ ) and short policies in .cursor/rules/*.mdc — do not paste full skills into rules. Both directories live in your project; this repo does not ship a .cursor/ folder. See docs/cursor-setup.md .

Install as a native plugin for skills and subagents. In affected Antigravity CLI releases, legacy command TOMLs are reported as converted but their wrapper commands are not discoverable; invoke the underlying namespaced skills directly. See docs/antigravity-setup.md .

Install from the repo:

Install from a local clone:

Install as native skills for auto-discovery, or add to GEMINI.md for persistent context. See docs/gemini-cli-setup.md .

Install from the repo:

Install from a local clone:

Add skill contents to your Windsurf rules configuration. See docs/windsurf-setup.md .

Copy skills to .opencode/skills/ (or ~/.config/opencode/skills/ ), add a project-local AGENTS.md , and use the built-in skill tool for agent-driven execution. Optional slash commands can be added under .opencode/commands/ .

See docs/opencode-setup.md .

Use agent definitions from agents/ as Copilot personas and skill content in .github/copilot-instructions.md . The lifecycle slash commands ( /spec , /plan , /build , /test , /review , /ship ) are Claude Code commands and do not appear in Copilot; invoke the skills by name ( /spec-driven-development , ...) instead. See docs/copilot-setup.md .

Using the standalone copilot CLI? Install it as a plugin — see docs/copilot-cli-setup.md .

Install as a native Codex plugin (Codex CLI v0.122+):

The first command registers the marketplace; the second installs the plugin. Codex reads the root skills/ directory directly through .codex-plugin/plugin.json . Once installed, invoke skills in chat using @ (e.g., @spec-driven-development ). See docs/codex-setup.md for local installation and troubleshooting.

Install natively with the built-in cmd skills command. Command Code clones the repo, discovers every SKILL.md , and installs into .commandcode/skills/ :

Installed skills show up in the TUI slash menu, e.g. /spec-driven-development . See docs/commandcode-setup.md .

Skills are plain Markdown - they work with any agent that accepts system prompts or instruction files. See docs/getting-started.md . Hosts that install the pack but aren't listed above are in docs/other-hosts.md .

Already installed? How you roll the pack out depends on your codebase. The Adoption Guide covers two paths: the full lifecycle from day one for a greenfield project, or an incremental, verification-first rollout for an established codebase.

The commands above are entry points. The pack includes 25 skills total — 24 lifecycle skills plus the using-agent-skills meta-skill. Each skill is a structured workflow with steps, verification gates, and anti-rationalization tables. You can also reference any skill directly.

Pre-configured specialist personas for targeted reviews:

See docs/agents.md for the decision matrix, orchestration rules, and how personas compose with skills and slash commands.

Quick-reference material that skills pull in when needed:

Every skill follows a consistent anatomy:

Key design choices:

The portable core stays in shared directories. Host-specific paths are native discovery conventions, not branding aliases; renaming or merging them would break the tools that scan those exact locations.

Tools without a checked-in adapter direct

</details>