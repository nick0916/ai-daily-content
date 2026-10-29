---
id: inbox_4deb5880
date: 2026-10-29
source_ref: "[[00-inbox/2026-10-29/0018-github-trending-agent-tools-expo-skills-3-567-90-59a3]]"
title: "expo/skills ⭐ 3,567(今日 +90)"
url: https://github.com/expo/skills
source: github-trending-agent-tools
published_at: 2026-10-29T00:18:09.695900+00:00
fetched_at: 2026-10-29T00:27:02.418249+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 編碼代理正確使用 Expo 與 EAS 的專屬知識包。 **Why** AI 代理對 Expo、EAS、React Native 的限制掌握有限，容易用錯 API 或流程。 **How** 以 SKILL.md 形式提供技能，可用 skills CLI 安裝，Claude Code 與 Codex 則用官方外掛市集，並搭配 Expo MCP Server 讓代理即時讀文件、執行安裝與觸發 EAS 建置。 **What** 由 Expo 官方出品，分為免費開源的 SDK 技能、付費 EAS 技能與實驗性技能三組；安裝指令為 npx skills@latest add expo/skills --skill '*'，採 MIT 授權，GitHub 星數 3,567（今日 +90）。"
key_points:
  - "Claude Code 與 Codex 用官方外掛市集安裝並自動更新；Cursor、OpenCode 等用 skills CLI 安裝"
  - "Expo MCP Server 可讀取最新 Expo 文件、執行 npx expo install、觸發與監控 EAS 建置、拉取 TestFlight 崩潰資料、在模擬器截圖"
  - "技能分為 Framework（免費）、Services（付費 EAS）、Experimental（位於 expo-experiments 外掛）三組"
tags: [expo, agent-skills, react-native, claude-code, mcp]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## expo/skills ⭐ 3,567(今日 +90)

讓 AI 編碼代理正確使用 Expo 與 EAS 的專屬知識包。

**Why** AI 代理對 Expo、EAS、React Native 的限制掌握有限，容易用錯 API 或流程。

**How** 以 SKILL.md 形式提供技能，可用 skills CLI 安裝，Claude Code 與 Codex 則用官方外掛市集，並搭配 Expo MCP Server 讓代理即時讀文件、執行安裝與觸發 EAS 建置。

**What** 由 Expo 官方出品，分為免費開源的 SDK 技能、付費 EAS 技能與實驗性技能三組；安裝指令為 npx skills@latest add expo/skills --skill '*'，採 MIT 授權，GitHub 星數 3,567（今日 +90）。

### 重點
- Claude Code 與 Codex 用官方外掛市集安裝並自動更新；Cursor、OpenCode 等用 skills CLI 安裝
- Expo MCP Server 可讀取最新 Expo 文件、執行 npx expo install、觸發與監控 EAS 建置、拉取 TestFlight 崩潰資料、在模擬器截圖
- 技能分為 Framework（免費）、Services（付費 EAS）、Experimental（位於 expo-experiments 外掛）三組

**原文：** [github-trending-agent-tools](https://github.com/expo/skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A collection of AI agent skills for working with Expo projects and Expo Application Services

How It Works

Installation

Updating

Try It

Skills Included

Expo MCP Server

FAQ

Feedback

License

Expo Skills

Skills CLI

Claude Code Plugin

Codex Plugin

Start Here

Framework (open source)

Services & paid distribution

Experimental

Which AI coding agents are supported?

Should I install the skills or the plugin?

What is the source of truth?

 

 

Official AI agent skills from the Expo team for building, deploying, upgrading, and debugging Expo apps.

Skills give AI agents focused Expo knowledge: when to use Expo APIs, how to structure common workflows, and which Expo, EAS, React Native, iOS, and Android constraints matter. Expo documentation, Expo CLI, and EAS CLI remain the source of truth; these skills help agents apply them correctly.

For Claude Code or Codex, install the plugin so updates are handled by the official plugin marketplace. For Cursor, OpenCode, and other AI coding agents, use the skills CLI.

Install all Expo skills with the skills CLI :

This selects every Expo skill without selecting every agent. The CLI will still ask where to install them; to target one agent directly, add --agent .

For most agents, this is the only install command you need. Run it from the project root, then restart or refresh your agent session so it can discover the installed SKILL.md files.

Install from the official Claude Code plugin marketplace:

You can also run /plugin install expo@claude-plugins-official inside Claude Code.

Install from the OpenAI-curated Codex marketplace:

You can also open /plugins in Codex and install expo from the OpenAI-curated marketplace.

Claude Code and Codex plugin installs are updated through their official plugin marketplaces.

For skills CLI installs, update installed skills with:

To update a single Expo skill, pass its name:

After installing, ask your agent Expo-specific questions like:

Agents choose the right skill from the task context and each skill's description.

Skills come in two groups so the free vs paid boundary is clear. Each skill's description carries the same label, and every services skill opens with a costs/plan-limits note.

Load this first for any Expo/EAS task, then route to the specific skill below.

Free, open-source Expo SDK and React Native skills.

Skills whose core purpose uses paid Expo Application Services (EAS).

Skills for Expo APIs that are not finalized. Content may change or be retired; skills graduate to the groups above when the underlying API stabilizes. These ship in the separate expo-experiments plugin (install it alongside expo ), or individually via the skills CLI.

Skills teach an agent how Expo work gets done. The Expo MCP server gives it live access to actually do that work: read the latest Expo docs on demand, install compatible dependencies with npx expo install , trigger and monitor EAS builds and workflows, pull crash data from TestFlight, and screenshot a running app in the simulator.

The expo plugin bundles this MCP configuration, so Claude Code and Codex plugin installs wire it up automatically. For other agents, or to add it on its own, follow the Expo MCP setup guide .

Use npx skills@latest add expo/skills --skill '*' for Cursor, OpenCode, GitHub Copilot, Windsurf, Gemini, Cline, AMP, Factory Droid, Antigravity, Kiro CLI, and similar AI coding tools.

Use the plugin for Claude Code or Codex; it stays updated through the plugin marketplace. Use npx skills@latest add expo/skills --skill '*' for Cursor, OpenCode, and other AI coding agents.

Expo documentation, Expo CLI, and EAS CLI are the source of truth. These skills teach agents how to apply Expo guidance in real projects.

Every skill includes instructions to submit specific, actionable feedback with npx --yes @expo/agent-cli@latest feedback .

MIT

"Build a native-feeling Expo Router screen with tabs, modals, and animations."

"Create an EAS workflow that builds previews on pull requests."

"Help me upgrade this app to the latest Expo SDK."

"Check whether this EAS Update rollout is healthy."

npx skills@latest add expo/skills --skill '*'

claude plugin install expo@claude-plugins-official

codex plugin add expo@openai-curated

npx skills@latest update

npx skills@latest update expo-router

</details>