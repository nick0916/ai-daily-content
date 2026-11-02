---
id: inbox_ae98c514
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-hermes-agent-releases-hermes-agent-v0-22-6-4a78]]"
title: "Hermes Agent v0.22.6"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.6
source: hermes-agent-releases
published_at: 2026-11-02T17:18:36+00:00
fetched_at: 2026-11-02T23:34:40.790553+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 發布 v0.22.6 修補版，把 v0.22.5 之後約 776 個 PR 打包成穩定版。 **What** 此版本涵蓋 CLI、Microsoft Store 應用、Docker 與 Hermes Cloud，期間共 3,448 個非 merge commit、4,316 個變更檔案與 385 個已關閉 issue。完整版本說明將隨 v0.23.0 發布。"
key_points:
  - "更新方式依管道而異：Microsoft Store 透過 Store 更新、CLI 執行 hermes update、Docker 使用 nousresearch/hermes-agent:stable 標籤"
  - "未在此版說明的功能包括 hermes webapp、opt-in 的 compression.prepare_ahead、hermes cron cancel 與 vault key 的 OS keychain 儲存"
  - "完整 release notes（涵蓋 v0.22.0 起的所有內容）將隨 v0.23.0 發布"
tags: [hermes-agent, release-notes, nous-research, cli]
topics: [agents.frameworks]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.22.6

Hermes Agent 發布 v0.22.6 修補版，把 v0.22.5 之後約 776 個 PR 打包成穩定版。

**What** 此版本涵蓋 CLI、Microsoft Store 應用、Docker 與 Hermes Cloud，期間共 3,448 個非 merge commit、4,316 個變更檔案與 385 個已關閉 issue。完整版本說明將隨 v0.23.0 發布。

### 重點
- 更新方式依管道而異：Microsoft Store 透過 Store 更新、CLI 執行 hermes update、Docker 使用 nousresearch/hermes-agent:stable 標籤
- 未在此版說明的功能包括 hermes webapp、opt-in 的 compression.prepare_ahead、hermes cron cancel 與 vault key 的 OS keychain 儲存
- 完整 release notes（涵蓋 v0.22.0 起的所有內容）將隨 v0.23.0 發布

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.22.6 
 Release Date: November 2, 2026 
 
 Patch release. This tag rolls up the ~776 PRs merged since v0.22.5 into a stable release for the GitHub release (CLI and installers), the Microsoft Store app, Docker and Hermes Cloud. Full curated notes for this window ship with v0.23.0. 
 

 About this release 
 Measured at commit f0d94882e89 , the window since v0.22.5 contains 3,448 non-merge commits across 4,316 changed files (+248,579 / −94,077), 776 merged PRs and 385 closed issues . 
 Also in the window, undocumented here on purpose: the Webapp served from the gateway's own listener ( hermes webapp , a Desktop Web Access pane to open it on your network or your own URL behind Nous sign-in, and Desktop plugins loading in a browser tab), /model reset to clear a session's model pin without losing history, per-skill locks against autonomous writes (lockable from the Desktop Capabilities pane), opt-in prepared compaction ( compression.prepare_ahead ), hermes cron cancel plus a per-job missed-run policy and a Stop button in the Desktop cron editor, /delegation choices saved for the next session, hermes migrate and setup moving Grok Bot and OpenBot users over, opt-in OS-keychain storage for the vault key, the catalog's requires_hermes enforced at plugin install and update, agent-picked ElevenLabs voices in text_to_speech , a pre_llm_call hook that can block a turn before inference, Desktop group chat rename, disband, mentions and attachment paste, every profile shown as a Desktop sidebar section, Telegram video notes, Slack emoji reactions in thread context, and resumable downloads in the package manager. 
 Full curated release notes for this window ship with v0.23.0 , which will document everything from v0.22.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.22.5...v0.22.6

</details>