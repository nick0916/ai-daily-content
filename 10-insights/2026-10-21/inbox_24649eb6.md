---
id: inbox_24649eb6
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-hermes-agent-releases-hermes-agent-v0-22-4-73d7]]"
title: "Hermes Agent v0.22.4"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.4
source: hermes-agent-releases
published_at: 2026-10-21T18:49:24+00:00
fetched_at: 2026-10-21T23:45:46.283114+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.22.4 為修補版，移除桌面版輸入框上方的建議按鈕。 **Why** 這些按鈕出現原因不明，多數在提示使用者設定 MCP 伺服器。 **What** 同時修正：無依賴外掛跳過空的同意提示、WhatsApp 登出後可安全重新配對、桌面版審核器不再誤報原型寫入、核准模式標籤跟隨 profile、發布建置的預檢時間加長；外掛目錄新增 bubblewrap、Singularity/Apptainer、mcp-serve、agent-importers（含 Cursor）等，Telegram Business 移至 Hermes Labs 社群層級。"
key_points:
  - "桌面版移除輸入框上方的建議按鈕（原多為催促設定 MCP 伺服器）及其專用輔助程式"
  - "無依賴外掛直接啟用，不再顯示空的同意提示；WhatsApp 登出後可安全重新配對"
  - "外掛目錄新增 mcp-serve（Hermes 作為 MCP 伺服器）、bubblewrap、Singularity/Apptainer、agent-importers（含 Cursor）"
tags: [hermes-agent, release, desktop, plugins, mcp]
topics: [agents.mcp, product_and_org.product]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.22.4

Hermes Agent v0.22.4 為修補版，移除桌面版輸入框上方的建議按鈕。

**Why** 這些按鈕出現原因不明，多數在提示使用者設定 MCP 伺服器。

**What** 同時修正：無依賴外掛跳過空的同意提示、WhatsApp 登出後可安全重新配對、桌面版審核器不再誤報原型寫入、核准模式標籤跟隨 profile、發布建置的預檢時間加長；外掛目錄新增 bubblewrap、Singularity/Apptainer、mcp-serve、agent-importers（含 Cursor）等，Telegram Business 移至 Hermes Labs 社群層級。

### 重點
- 桌面版移除輸入框上方的建議按鈕（原多為催促設定 MCP 伺服器）及其專用輔助程式
- 無依賴外掛直接啟用，不再顯示空的同意提示；WhatsApp 登出後可安全重新配對
- 外掛目錄新增 mcp-serve（Hermes 作為 MCP 伺服器）、bubblewrap、Singularity/Apptainer、agent-importers（含 Cursor）

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.22.4 
 Release Date: October 21, 2026 
 
 Patch release. Desktop stops showing suggestion pills above the composer, plus small plugin and dashboard fixes, for the CLI and installer, the Microsoft Store app, Docker and Hermes Cloud. 
 

 Fixes 
 
 Desktop no longer shows suggestion pills above the composer. The pills appeared for no clear reason, mostly nudging you to set up MCP servers. They and the helpers that only they used are gone. ( #142559 ) 
 Plugins that install nothing skip the dependency consent step. A plugin that declares no dependencies, or whose pyproject.toml installs nothing, now enables without an empty consent prompt. ( #142569 ) 
 Dashboard: WhatsApp can be safely re-paired after logging out. ( #142439 ) 
 Desktop plugin review: the surface lint no longer flags prototype writes; reviewers check them by hand. ( #142586 ) 
 Desktop: the approval-mode chip follows the active profile's mode. ( #142565 ) 
 Release builds: the desktop bundle's pre-build check gets enough time to verify archived build inputs when storage is slow. ( #142623 ) 
 
 Also new in the plugin catalog: bubblewrap (bwrap terminal backend on Linux), Singularity/Apptainer, mcp-serve (Hermes as an MCP server), agent-importers ( hermes import-agent , now with Cursor), inbox and workflow-record from Hermes Labs. Telegram Business moves to the Hermes Labs community tier. 
 About this release 
 Measured at commit 4d04303818b , the window since v0.22.3 contains 14 non-merge commits across 82 changed files (+1,475 / −3,022) and 13 merged PRs . 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.22.3...v0.22.4

</details>