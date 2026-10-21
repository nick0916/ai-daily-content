---
id: inbox_36fa5446
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-hermes-agent-releases-hermes-agent-v0-22-3-7acd]]"
title: "Hermes Agent v0.22.3"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.3
source: hermes-agent-releases
published_at: 2026-10-21T12:21:11+00:00
fetched_at: 2026-10-21T23:45:46.283378+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把約 620 個已合併 PR 的改動打包成 Hermes Agent v0.22.3 穩定補丁版。 **What** 區間內共 2,911 個非 merge commit、4,206 個變更檔案（+360,278 / −64,308）、約 620 個合併 PR 與 326 個關閉 issue。原文列出未在本文件詳述的功能，包括 MCP 進度通知即時串流、外掛可宣告並由 Hermes 登入與刷新的 OAuth 用戶端、hermes plugins update、本地執行環境的 Nemotron 3.5 Bolt 與單槽 DFlash 草稿、session 自動清理改回 opt-in；完整說明將於 v0.23.0 發布。"
key_points:
  - "區間內 2,911 個非 merge commit、4,206 個檔案變更，約 620 個合併 PR 與 326 個關閉 issue"
  - "未詳述功能含 MCP 進度通知即時串流、外掛 OAuth 用戶端、hermes plugins update"
  - "完整 release notes 將於 v0.23.0 補上，涵蓋 v0.22.0 之後的所有內容"
tags: [hermes-agent, release-rollup, mcp, plugins, local-runtime]
topics: [agents.mcp, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.22.3

把約 620 個已合併 PR 的改動打包成 Hermes Agent v0.22.3 穩定補丁版。 **What** 區間內共 2,911 個非 merge commit、4,206 個變更檔案（+360,278 / −64,308）、約 620 個合併 PR 與 326 個關閉 issue。原文列出未在本文件詳述的功能，包括 MCP 進度通知即時串流、外掛可宣告並由 Hermes 登入與刷新的 OAuth 用戶端、hermes plugins update、本地執行環境的 Nemotron 3.5 Bolt 與單槽 DFlash 草稿、session 自動清理改回 opt-in；完整說明將於 v0.23.0 發布。

### 重點
- 區間內 2,911 個非 merge commit、4,206 個檔案變更，約 620 個合併 PR 與 326 個關閉 issue
- 未詳述功能含 MCP 進度通知即時串流、外掛 OAuth 用戶端、hermes plugins update
- 完整 release notes 將於 v0.23.0 補上，涵蓋 v0.22.0 之後的所有內容

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.22.3 
 Release Date: October 21, 2026 
 
 Patch release. This tag rolls up the ~620 PRs merged since v0.22.2 into a stable release for the CLI and installer, the Microsoft Store app, Docker and Hermes Cloud. Full curated notes for this window ship with v0.23.0. 
 

 About this release 
 Measured at commit 5b147ab036d , the window since v0.22.2 contains 2,911 non-merge commits across 4,206 changed files (+360,278 / −64,308), about 620 merged PRs and 326 closed issues . 
 Also in the window, undocumented here on purpose: MCP progress notifications streamed as live tool progress, a refreshed classic CLI layout (glyph transcript, status line under the composer, two-line header), OAuth clients that plugins declare and Hermes signs in and refreshes, hermes plugins update offering every available plugin update plus an Update button for git-installed plugins in Desktop, steering and editing a queued prompt from Desktop, a guided subagent model and provider picker in Desktop, a live /loop countdown row in the CLI and TUI, opt-in Telegram DM topic transfer, a post_compaction plugin hook, a capabilities catalog, the Microsoft Store build going live automatically when a release publishes, session auto-prune back to opt-in with a one-time prompt when disk runs low, Nemotron 3.5 Bolt and one-slot DFlash drafts in the local runtime, and dozens of new plugin catalog entries. 
 Full curated release notes for this window ship with v0.23.0 , which will document everything from v0.22.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.22.2...v0.22.3

</details>