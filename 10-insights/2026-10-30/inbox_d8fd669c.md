---
id: inbox_d8fd669c
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/0035-github-trending-agent-tools-thedotmack-claude-mem-104-784-336-13e9]]"
title: "thedotmack/claude-mem ⭐ 104,784(今日 +336)"
url: https://github.com/thedotmack/claude-mem
source: github-trending-agent-tools
published_at: 2026-10-30T00:35:44.429592+00:00
fetched_at: 2026-10-30T00:44:19.937145+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓編碼 agent 跨 session 保留專案脈絡的記憶外掛。 **Why** 每次 session 結束後，agent 會遺失先前的工作脈絡。 **How** 自動擷取工具使用紀錄，以 AI 壓縮成摘要，並在未來 session 注入相關脈絡；提供 4 個 MCP 搜尋工具，採三層工作流。 **What** 支援 Claude Code、Codex、Gemini、Copilot、OpenCode 等；Claude Code 以 `npx claude-mem install` 安裝；GitHub 星數 104,784，今日 +336。"
key_points:
  - "擷取 session 中的工具使用與觀察紀錄，壓縮後注入未來 session，讓 agent 延續專案知識。"
  - "安裝指令為 `npx claude-mem install`；文件提醒 `npm install -g claude-mem` 只安裝 SDK，不會註冊 hooks 與 worker 服務。"
  - "記憶後端可選 claude-mem 雲端（文中提及 30 天免費試用）、自帶 OpenRouter 或 Gemini key，或使用 Anthropic 方案。"
tags: [agent-memory, claude-code, mcp-tools, context-persistence, trending-oss]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## thedotmack/claude-mem ⭐ 104,784(今日 +336)

讓編碼 agent 跨 session 保留專案脈絡的記憶外掛。

**Why** 每次 session 結束後，agent 會遺失先前的工作脈絡。

**How** 自動擷取工具使用紀錄，以 AI 壓縮成摘要，並在未來 session 注入相關脈絡；提供 4 個 MCP 搜尋工具，採三層工作流。

**What** 支援 Claude Code、Codex、Gemini、Copilot、OpenCode 等；Claude Code 以 `npx claude-mem install` 安裝；GitHub 星數 104,784，今日 +336。

### 重點
- 擷取 session 中的工具使用與觀察紀錄，壓縮後注入未來 session，讓 agent 延續專案知識。
- 安裝指令為 `npx claude-mem install`；文件提醒 `npm install -g claude-mem` 只安裝 SDK，不會註冊 hooks 與 worker 服務。
- 記憶後端可選 claude-mem 雲端（文中提及 30 天免費試用）、自帶 OpenRouter 或 Gemini key，或使用 Anthropic 方案。

**原文：** [github-trending-agent-tools](https://github.com/thedotmack/claude-mem)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Persistent Context Across Sessions for Every Agent – Captures everything your agent does during sessions, compresses it with AI, and injects relevant context back into future sessions. Works with Claude Code, OpenClaw, Codex, Gemini, Hermes, Copilot, OpenCode + More

 

Quick Start

Documentation

How It Works

MCP Search Tools

System Requirements

Configuration

Restart Claude Code to apply the new mode configuration.

Development

Troubleshooting

Bug Reports

Contributing

License

Support

🦞 OpenClaw Gateway

Getting Started

Best Practices

Architecture

Configuration & Development

Windows Setup Notes

Mode & Language Configuration

What About CMEM?

 

 🇨🇳 中文 • 🇹🇼 繁體中文 • 🇯🇵 日本語 • 🇵🇹 Português • 🇧🇷 Português • 🇰🇷 한국어 • 🇪🇸 Español • 🇩🇪 Deutsch • 🇫🇷 Français • 🇮🇱 עברית • 🇸🇦 العربية • 🇷🇺 Русский • 🇵🇱 Polski • 🇨🇿 Čeština • 🇳🇱 Nederlands • 🇹🇷 Türkçe • 🇺🇦 Українська • 🇻🇳 Tiếng Việt • 🇵🇭 Tagalog • 🇮🇩 Indonesia • 🇹🇭 ไทย • 🇮🇳 हिन्दी • 🇧🇩 বাংলা • 🇵🇰 اردو • 🇷🇴 Română • 🇸🇪 Svenska • 🇮🇹 Italiano • 🇬🇷 Ελληνικά • 🇭🇺 Magyar • 🇫🇮 Suomi • 🇩🇰 Dansk • 🇳🇴 Norsk 

 

 

 Quick Start • How It Works • Search Tools • Documentation • Configuration • Troubleshooting • License 

Claude-Mem seamlessly preserves context across sessions by automatically capturing tool usage observations, generating semantic summaries, and making them available to future sessions. This enables Claude to maintain continuity of knowledge about projects even after sessions end or reconnect.

Install claude-mem for Grok Bot:

Grok Bot has no host hooks, so we watch the chat log files. Default is CMEM Pro, the hosted memory. Local observer is opt-in: --provider host . Installing this plugin does not install Cursor.

Awareness push pilot (LFG + Orifice): needle observations ( decision , bugfix , security_alert , sensitive ) are appended as dated - YYYY-MM-DD [awareness] ... lines into that bot's memory/log/YYYY-MM.md . Grok Bot already re-reads the log from disk. This does not write profile.md , user-memory, or project memory. Disable with CLAUDE_MEM_GROK_BOT_AWARENESS_ENABLED=false .

Install with a single command:

The installer sets everything up first, then asks you to sign in to claude-mem in your browser (email magic link — no card required). Signing in provisions a memory key for your account and unlocks the claude-mem observer with a 30 Day Free Trial : memory runs off-plan, so you get up to 100% more usage from your plan. When the free trial ends, memory automatically falls back to your Anthropic plan unless you subscribe. After sign-in you pick your memory provider — the claude-mem observer, your own OpenRouter or Gemini key, or your Anthropic plan.

Prefer to skip the sign-in? Pass an explicit --provider flag, set CLAUDE_MEM_ONLINE_OPTIN=false , or run in CI/non-interactive shells — the installer completes without any account interaction.

Or install for OpenCode:

This works with OpenCode 1.3.4 or later, including OpenCode 2. Restart OpenCode after installing.

Or install for T3 Code (Codex and Claude Code providers):

The installer discovers T3 Code's enabled providers, registers native Claude-Mem plugins in their configured homes, and supports T3-managed Codex. Restart T3 Code, trust the provider's hooks when prompted, and start a new thread. See the T3 Code integration guide for custom server settings, status, and removal.

Or install for Antigravity CLI ( setup guide ):

Or install for OMP (Oh My Pi):

Or install the native Pi extension or DeepSeek Harness plugin:

Pi and DeepSeek Harness use the worker runtime. See native harness setup for capture, recall, and troubleshooting.

Or install from the plugin marketplace inside Claude Code:

Restart Claude Code. Context from previous sessions will automatically appear in new sessions.

Note: Claude-Mem is also published on npm, but npm install -g claude-mem installs the SDK/library only — it does not register the plugin hooks or set up the worker service. Always install via npx claude-mem install or the /plugin commands above.

Install claude-mem as a persistent memory plugin on OpenClaw gateways with a single command:

The installer handles dependencies, plugin setup, AI provider configuration, worker startup, and optional real-time observation feeds to Telegram, Discord, Slack, and more. See the OpenClaw Integration Guide for details.

Key Features:

📚 View Full Documentation - Browse on official website

Core Components:

See Architecture Overview for details.

Claude-Mem provides intelligent memory search through 4 MCP tools following a token-efficient 3-layer workflow pattern :

The 3-Layer Workflow:

How It Works:

Available MCP Tools:

Example Usage:

See Search Tools Guide for detailed examples.

If you see an error like:

Make sure Node.js and npm are installed and added to your PATH. Download the latest Node.js installer from https://nodejs.org and restart your terminal after installation.

Claude Code hooks do not need Git Bash. Each hook runs claude-mem directly, and npx claude-mem install places that launcher at %LOCALAPPDATA%\claude-mem\bin\claude-mem.exe and adds the folder to your user Path. Restart your terminal or IDE afterwards so Claude Code picks up the new Path. If hooks report Executable not found in $PATH: "claude-mem" , run npx claude-mem doctor and see Troubleshooting .

Settings are managed in ~/.claude-mem/settings.json (auto-created with defaults on first run). Configure AI model, worker port, data directory, log level, and context injection settings.

To include observations from every harness in Claude Code and Codex SessionStart context, set "CLAUDE_MEM_SESSION_START_INCLUDE_ALL_SOURCES": "true" in that file, or enable Include all sources at session start in the viewer settings. The default is "false" , which limits startup context to the current harness. The observation count limit still applies across the selected sources.

See the Configuration Guide for all available settings and examples.

Claude-Mem supports multiple workflow modes and languages via the CLAUDE_MEM_MODE setting.

This option controls both:

Edit your settings file at ~/.claude-mem/settings.json :

Modes are defined in plugin/modes/ . To see all available modes locally:

Language-specific modes follow the patt

</details>