---
id: inbox_24ae0697
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-hermes-agent-releases-hermes-agent-v0-22-5-413c]]"
title: "Hermes Agent v0.22.5"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.5
source: hermes-agent-releases
published_at: 2026-10-23T05:28:45+00:00
fetched_at: 2026-10-24T03:56:32.977448+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 發布 v0.22.5 修補版，把約 81 個 PR 打包上線。 **What** 版本於 2026-10-22 發布，涵蓋 231 個非 merge commit、804 個檔案變更（+35,212／−17,885）與 30 個已關閉 issue；完整發布說明將隨 v0.23.0 提供。更新方式：CLI 執行 hermes update，Docker／Hermes Cloud 使用 nousresearch/hermes-agent:stable，Microsoft Store 版經商店更新。"
key_points:
  - "外掛化：hermes mcp serve 與 Singularity backend 從 core 移到 plugin，setup 偵測到其他 agent 時會提供匯入"
  - "新增可插拔 delegation backend，可依 model map 或 profile 分派 subagent，並可按 session 切換"
  - "Nous 登入流程重做：免費 guest 轉為正式帳號，connectors 改為引導登入而非開啟 guest"
tags: [hermes-agent, patch-release, plugin-architecture, subagent-delegation, release-notes]
topics: [agents.frameworks, agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.22.5

Hermes Agent 發布 v0.22.5 修補版，把約 81 個 PR 打包上線。 **What** 版本於 2026-10-22 發布，涵蓋 231 個非 merge commit、804 個檔案變更（+35,212／−17,885）與 30 個已關閉 issue；完整發布說明將隨 v0.23.0 提供。更新方式：CLI 執行 hermes update，Docker／Hermes Cloud 使用 nousresearch/hermes-agent:stable，Microsoft Store 版經商店更新。

### 重點
- 外掛化：hermes mcp serve 與 Singularity backend 從 core 移到 plugin，setup 偵測到其他 agent 時會提供匯入
- 新增可插拔 delegation backend，可依 model map 或 profile 分派 subagent，並可按 session 切換
- Nous 登入流程重做：免費 guest 轉為正式帳號，connectors 改為引導登入而非開啟 guest

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.22.5 
 Release Date: October 22, 2026 
 
 Patch release. This tag rolls up the ~81 PRs merged since v0.22.4 into a stable release for the GitHub release (CLI and installers), the Microsoft Store app, Docker and Hermes Cloud. Full curated notes for this window ship with v0.23.0. 
 

 About this release 
 Measured at commit bf0203a794a , the window since v0.22.4 contains 231 non-merge commits across 804 changed files (+35,212 / −17,885), 81 merged PRs and 30 closed issues . 
 Also in the window, undocumented here on purpose: Nous sign-in reworked (every sign-in is the plain device login, the free-tier guest hands over to your account, the result shows who signed in, connectors offer sign-in instead of opening a guest), hermes update holding back a stable release it refuses instead of offering it, Windows hermes update no longer stuck on the old launcher after a Python repin, usage-window plan support (plan gauges, limit cards and model-switch recovery for window-based plans), pluggable delegation backends (route subagents by model map or profile, switchable per session), plugin slash commands that can ask you to pick an option, hermes import-agent , OpenClaw migration, hermes mcp serve and the Singularity backend moving out of core into plugins (setup offers the importer when it finds another agent), Desktop drag-to-pin in the sidebar and one-click plugin installs with tier badges, the Electron 44 upgrade, Pillow 13 and a batch of dependency security bumps, a clear message when a chat's working folder is gone, hermes update recovering paused gateways after a damaged .git , long Claude DirectSDK answers no longer cut off by the stall timer, Desktop group chats showing which bot is working again, and the experimental webhook-mode MCP events client. 
 Full curated release notes for this window ship with v0.23.0 , which will document everything from v0.22.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.22.4...v0.22.5

</details>