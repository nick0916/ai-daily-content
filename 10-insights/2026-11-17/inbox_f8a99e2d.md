---
id: inbox_f8a99e2d
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2318-github-trending-agent-tools-google-labs-code-stitch-skills-10-080-35-1909]]"
title: "google-labs-code/stitch-skills ⭐ 10,080(今日 +350)"
url: https://github.com/google-labs-code/stitch-skills
source: github-trending-agent-tools
published_at: 2026-11-17T23:18:24.242549+00:00
fetched_at: 2026-11-17T23:29:56.397619+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 Google Stitch 的設計流程包成可供多種 coding agent 使用的 Agent Skills 套件。 **Why** 需要讓各種 coding agent 都能使用 Stitch MCP 伺服器提供的設計流程。 **How** 依 Agent Skills 開放標準撰寫，分為 stitch-design、stitch-build、stitch-utilities 三組 plugin，可用 npx plugins 或 npx skills 安裝。 **What** 涵蓋 generate-design、extract-design-md、react-components、shadcn-ui、remotion、design-md、taste-design 等技能；相容 Codex、Antigravity、Gemini CLI、Claude Code、Cursor、OpenCode；README 註明這不是 Google 官方支援的產品；今日 GitHub 星數 10,080（+350）。"
key_points:
  - "需先設定 Stitch MCP 伺服器；OpenCode 要求 skill 的 name 為 kebab-case 且與資料夾名稱一致才能載入"
  - "三組 plugin：design（code-to-design、generate-design 等）、build（react-components、react-native、shadcn-ui 等）、utilities（design-md、enhance-prompt、stitch-loop 等）"
  - "Claude Code 安裝指令：npx plugins add google-labs-code/stitch-skills --scope project --target claude-code"
tags: [google-stitch, agent-skills, mcp, design-to-code, claude-code]
topics: [agents.coding_agents, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## google-labs-code/stitch-skills ⭐ 10,080(今日 +350)

把 Google Stitch 的設計流程包成可供多種 coding agent 使用的 Agent Skills 套件。

**Why** 需要讓各種 coding agent 都能使用 Stitch MCP 伺服器提供的設計流程。

**How** 依 Agent Skills 開放標準撰寫，分為 stitch-design、stitch-build、stitch-utilities 三組 plugin，可用 npx plugins 或 npx skills 安裝。

**What** 涵蓋 generate-design、extract-design-md、react-components、shadcn-ui、remotion、design-md、taste-design 等技能；相容 Codex、Antigravity、Gemini CLI、Claude Code、Cursor、OpenCode；README 註明這不是 Google 官方支援的產品；今日 GitHub 星數 10,080（+350）。

### 重點
- 需先設定 Stitch MCP 伺服器；OpenCode 要求 skill 的 name 為 kebab-case 且與資料夾名稱一致才能載入
- 三組 plugin：design（code-to-design、generate-design 等）、build（react-components、react-native、shadcn-ui 等）、utilities（design-md、enhance-prompt、stitch-loop 等）
- Claude Code 安裝指令：npx plugins add google-labs-code/stitch-skills --scope project --target claude-code

**原文：** [github-trending-agent-tools](https://github.com/google-labs-code/stitch-skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A library of Agent Skills designed to work with the Stitch MCP server. Each skill follows the Agent Skills open standard, for compatibility with coding agents such as Antigravity, Gemini CLI, Claude Code, Cursor.

Stitch Design Skills

Quick Start

Prerequisites

Available Plugins

Repository Structure

Adding New Skills

1. Install Plugins (Recommended)

2. Install Skills Selectively

Design ( stitch-design )

Build ( stitch-build )

Utilities ( stitch-utilities )

Great candidates for new skills

A collection of agent skills and plugins for Google Stitch , following the Agent Skills open standard. Compatible with coding agents such as Codex, Antigravity, Gemini CLI, Claude Code, Cursor, and OpenCode (manual install).

The fastest way to set up the full Stitch plugin suite globally.

Add the Stitch Skills marketplace, then install the plugins you need.

[!TIP]
The --sparse flags are optional — they limit the checkout to only the
listed paths for a faster clone. Omit them to pull the entire repository.

Navigate to Settings → Plugin Marketplaces → Add and fill in:

Once the marketplace is registered, install any combination of:

OpenCode does not use npx plugins / npx skills or the Codex/Claude marketplace layout.
Install skills and the Stitch MCP server manually:

1. Skills — copy the skill folders you need into a discoverable path:

OpenCode also discovers .claude/skills/ and .agents/skills/ (see OpenCode skills docs ).

Naming: OpenCode requires skill name frontmatter to be lowercase kebab-case and match the directory name. Skills that use stitch::... names (or other non-kebab forms) need the name field and folder renamed before OpenCode will load them. Extra frontmatter such as allowed-tools is ignored.

2. Stitch MCP — add a remote MCP entry in project opencode.json or ~/.config/opencode/opencode.json after completing the Stitch MCP setup :

Replace YOUR_STITCH_MCP_URL with the endpoint from the Stitch MCP setup flow (credentials/env vars from that guide still apply).

Tool names inside skill instructions may differ from OpenCode builtins ( webfetch / bash instead of web_fetch / run_command ). Prefer the OpenCode tool names when adapting a skill for OpenCode.

Choose only the specific skills you need.

Important

Stitch Design Skills often have inter-dependencies. If you choose to install skills selectively, ensure you include all required dependencies.

You can run the following commands to see the help documentation for plugins and skills:

These skills require the Stitch MCP server to be configured and running in your agent's environment. Make sure you have followed the Stitch MCP Setup Instructions to register the server and set up appropriate environment variables and credentials.

Docs navigation: If a link on stitch.withgoogle.com/docs redirects incorrectly, open the target path under the same host (e.g. https://stitch.withgoogle.com/docs/learn/device-types/ ).

Core design workflows for creating, managing, and optimizing designs within Stitch.

Code generation, framework integration, and asset compilation from Stitch designs.

Supporting tools for enhancing prompts, generating design specs, and enforcing design standards.

Each skill follows the Agent Skills standard:

All new skills need to follow the file structure above to implement the Agent Skills open standard.

This is not an officially supported Google product. This project is not eligible for the Google Open Source Software Vulnerability Rewards Program .

stitch-design — design-focused skills

stitch-build — build and component skills

stitch-utilities — utility and helper skills

Validation : Skills that convert Stitch HTML to other UI frameworks and validate the syntax.

Decoupling Data : Skills that convert static design content into external mock data files.

Generate Designs : Skills that generate new design screens in Stitch from a given set of data.

codex plugin marketplace add google-labs-code/stitch-skills --ref main \
 --sparse .agents/plugins \
 --sparse plugins/stitch-design \
 --sparse plugins/stitch-build \
 --sparse plugins/stitch-utilities

# Claude Code — installs into the current project npx plugins add google-labs-code/stitch-skills --scope project --target claude-code

# Cursor — installs into the current workspace npx plugins add google-labs-code/stitch-skills --scope workspace --target cursor

# Project-local (recommended) mkdir -p .opencode/skills
cp -R plugins/stitch-design/skills/generate-design .opencode/skills/generate-design # repeat for other skills under plugins/*/skills/

{ "$schema" : " https://opencode.ai/config.json " , "mcp" : { "stitch" : { "type" : " remote " , "url" : " YOUR_STITCH_MCP_URL " , "enabled" : true }
 }
}

npx skills add google-labs-code/stitch-skills

npx plugins --help

npx skills --help

plugins/
├── stitch-design/ — Core design workflow plugin
│ ├── plugin.json
│ └── skills/
│ ├── code-to-design/
│ ├── generate-design/
│ ├── manage-design-system/
│ ├── extract-design-md/
│ ├── extract-static-html/
│ └── upload-to-stitch/
├── stitch-build/ — Code generation & build plugin
│ ├── plugin.json
│ └── skills/
│ ├── react-components/ — stitch::react-components
│ ├── react-native/
│ ├── react-vite-dashboard/
│ ├── remotion/
│ └── shadcn-ui/
└── stitch-utilities/ — Design utilities & assistants plugin
 ├── plugin.json
 └── skills/
 ├── design-md/
 ├── enhance-prompt/
 ├── stitch-loop/
 └── taste-design/

skills/ /
├── SKILL.md — The "Mission Control" for the agent
├── scripts/ — Executable enforcers (Validation & Networking)
├── resources/ — The knowledge base (Checklists & Style Guides)
└── examples/ — The "Gold Standard" syntactically valid references

</details>