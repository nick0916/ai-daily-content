---
id: inbox_75a4b16e
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/0125-github-trending-agent-tools-affaan-m-ecc-289-869-896-18d9]]"
title: "affaan-m/ECC ⭐ 289,869(今日 +896)"
url: https://github.com/affaan-m/ECC
source: github-trending-agent-tools
published_at: 2026-10-27T01:25:27.449568+00:00
fetched_at: 2026-10-27T01:38:32.586658+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "為 Claude Code、Codex 等 coding agent 提供一套含規劃、測試、獨立審查與記憶的工程系統與工具箱。 **Why** 單靠 agent 寫程式不足以保證工程品質，每次都得在 prompt 裡重建流程。 **How** 讓 agent 先規劃再建置、以測試驗證、從新的 context 審查自己的成果，並把重複成功的做法沉澱為可重用的 skill 與 workflow。 **What** 倉庫 README 列出 71 個 agents、311 個 skills、97 個 legacy command shims，附 hooks、rules、memory 與 AgentShield 安全掃描；ECC 2.2 提供 Claude Code、Codex、Kimi Code 的引導式安裝。GitHub 星數約 289,869（今日 +896）。"
key_points:
  - "規模：71 個 agents、311 個 skills、97 個 legacy command shims，並含 hooks、rules、memory 與 AgentShield"
  - "平台支援分級：Claude Code 為主，Codex 與 Qoder 為原生 plugin；Cursor、OpenCode、Gemini 等為 capability-limited adapter"
  - "安裝：需 Node.js 18+，Claude plugin 另需 Git 與 Claude Code 2.1+；README 提醒只從官方管道（plugin slug ecc@ecc 等）安裝"
tags: [claude-code, agent-harness, skills, agent-workflow, codex]
topics: [agents.coding_agents, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## affaan-m/ECC ⭐ 289,869(今日 +896)

為 Claude Code、Codex 等 coding agent 提供一套含規劃、測試、獨立審查與記憶的工程系統與工具箱。

**Why** 單靠 agent 寫程式不足以保證工程品質，每次都得在 prompt 裡重建流程。

**How** 讓 agent 先規劃再建置、以測試驗證、從新的 context 審查自己的成果，並把重複成功的做法沉澱為可重用的 skill 與 workflow。

**What** 倉庫 README 列出 71 個 agents、311 個 skills、97 個 legacy command shims，附 hooks、rules、memory 與 AgentShield 安全掃描；ECC 2.2 提供 Claude Code、Codex、Kimi Code 的引導式安裝。GitHub 星數約 289,869（今日 +896）。

### 重點
- 規模：71 個 agents、311 個 skills、97 個 legacy command shims，並含 hooks、rules、memory 與 AgentShield
- 平台支援分級：Claude Code 為主，Codex 與 Qoder 為原生 plugin；Cursor、OpenCode、Gemini 等為 capability-limited adapter
- 安裝：需 Node.js 18+，Claude plugin 另需 Git 與 Claude Code 2.1+；README 提醒只從官方管道（plugin slug ecc@ecc 等）安裝

**原文：** [github-trending-agent-tools](https://github.com/affaan-m/ECC)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The agent harness performance optimization system. Skills, instincts, memory, security, and research-first development for Claude Code, Codex, Opencode, Cursor and beyond.

ECC

Install with Claude Code

Install ECC

Advanced Install Options

Start Using ECC

Self-Hosted Models and Custom Endpoints

What's New

What's Inside

Key Concepts

Guides

Why Choose ECC?

Platform Support

Token Optimization

Requirements

Security

Ecosystem Tools

Troubleshooting

Running Tests

Background

Community and Project

Links

License

Recommended: universal guided setup

Pick one path only (per harness)

Claude Code details

Codex App and CLI

Qoder CLI and IDE

Other agents and editors

Low-context / no-hooks path

Find the right components first

Reset / Uninstall ECC

Self-host Kimi with ECC + Itô compute

Itô compute CLI bridge

v2.0.0: The Agent Harness Operating System (Jun 2026)

Agents

Skills

Hooks

Rules

TDD: Test-Driven Development

Skills keep the context focused

Share context between harnesses

Cross-tool capability map

Claude Code CLI version

Important: hooks auto-loading behavior

Option A: Local Analysis (Built-in)

Option B: GitHub App (Advanced)

 

 

 Language: English | العربية | Português (Brasil) | 简体中文 | 繁體中文 | 日本語 | 한국어 | Türkçe | Русский | Tiếng Việt | ไทย | Deutsch | Español | Українська | Polski | বাংলা 

 

 

 

 

Warning

Official sources only. Install ECC only from verified channels: the GitHub repository github.com/affaan-m/ECC , the npm packages ecc-universal and ecc-agentshield , the GitHub App , the plugin slug ecc@ecc , and the project website ecc.tools . Third-party re-uploads and unofficial mirrors are not maintained or reviewed by the project and may contain malware.

Use the guided setup or native plugin commands . Both install the same ecc@ecc plugin. Choose one and do not stack a full manual Claude install on top.

OSS stays free. This repo is MIT-licensed forever. ECC Pro is the hosted GitHub App for private repos. Sponsors and Pro subscribers fund the work. That's why a single maintainer ships weekly across 7 harnesses.

Partners & sponsors

 

Past sponsors: Atlas Cloud · Mike Morgan (inactive)

Community sponsors: @jasonwu513 · @1anter · @massimotodaro · @meadmccabe

Become a Sponsor · Sponsor Tiers · Sponsorship Program

Jump to install ↓

Your agent can write code, but ECC gives it a coordinated engineering system and toolbox: it plans before it builds, verifies changes with tests, reviews its own work from a fresh context, remembers what matters, and turns repeated wins into reusable skills and workflows.

Instead of rebuilding that process in every prompt, you install it once and make it part of how your agent works.

Optimize the context window. Persist everything else.

ECC is MIT-licensed open source. It works best with Claude Code today, has native Codex and Qoder plugin paths, and provides capability-limited adapters for Cursor, OpenCode, Gemini, Zed, GitHub Copilot, Antigravity, Qwen, and other harnesses. See the support status matrix before assuming feature parity.

Access to 71 agents, 311 skills, and 97 legacy command shims, plus hooks, rules, memory, continuous learning, and AgentShield security scanning. The agents are specialized for planning, review, build repair, security, architecture, and domain work.

 

Important

ECC 2.2 includes guided package setup for Claude Code, Codex, and Kimi Code.
The universal package requires Node.js 18 or newer. Claude plugin setup also
requires Git and Claude Code 2.1 or newer on PATH .

For Claude Code plugin setup, updates, scope changes, and hook-profile changes:

If you are new to command-line tools, use this copy-and-paste path:

Install Node.js 18 or newer, Git, and Claude Code.

Open PowerShell from the Windows Start menu.

Confirm that each prerequisite is available:

Run the guided installer:

For a typical personal setup, choose Global user , choose Standard hooks, and confirm.

Start a new Claude Code session and run /plugin list to verify that ecc@ecc is enabled.

This path does not require cloning the repository. If any prerequisite command is not found, install or repair that prerequisite before rerunning ECC setup.

If npm reports a version or cache error, confirm the registry version before retrying:

ECC 2.2 supports the same guided setup through modern package runners:

The examples select the published ECC 2.2.3 release , matching this repository's release version. A version pin is not a security audit or an integrity check. Review the release source and registry integrity before running package code; use a reviewed checkout for unreleased changes.

Yarn Classic 1 does not provide yarn dlx ; use npx , install the package globally, or upgrade Yarn for a temporary one-shot run.

The wizard inventories the official marketplace and every native Claude install scope before making changes, then installs, updates, or safely moves ecc@ecc to the scope you choose. Rerun the same command whenever you want to update ECC, change scope, or change its hook profile. This setup wizard currently configures the Claude Code plugin; use the multi-harness wizard below for Codex or Kimi Code.

To configure more than one coding agent in one reviewed flow, use the multi-harness wizard:

It lets you select any combination of Claude Code, Codex, and Kimi Code, shows each install channel and destination, preflights every selection before the first write, and asks for one final confirmation.

For automation, make every provider-specific choice explicit:

Verify the native guided Codex path and managed Kimi path without writing first:

Additional package-name commands are also available through the 2.2 alias:

Do not use npx ecc-install --profile minimal --target claude : ecc-install is a binary name inside ecc-universal , not a separately published npm package.

ECC also ships advanced managed adapters for cursor , antigravity , gemini , opencode , codebuddy , joycode , qwen , zed , hermes , and openclaw . Those targets still use their documented ecc install --target ... paths until each adapter has passed the guided collision, update, rep

</details>