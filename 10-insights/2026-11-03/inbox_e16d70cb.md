---
id: inbox_e16d70cb
date: 2026-11-03
source_ref: "[[00-inbox/2026-11-03/2348-hermes-agent-releases-hermes-agent-v0-22-7-379a]]"
title: "Hermes Agent v0.22.7"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.7
source: hermes-agent-releases
published_at: 2026-11-03T21:53:16+00:00
fetched_at: 2026-11-03T23:57:13.836473+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.22.7 是整合約 174 個已合併 PR 的補丁版本。 **What** 同步發布於 GitHub（CLI 與安裝程式）、Microsoft Store、Docker 與 Hermes Cloud；另有群聊 lead routing、Kanban 釘選看板、Telegram 接入 Team Gateway 等未在本版文件化的功能，完整說明待 v0.23.0。"
key_points:
  - "彙整 v0.22.6 以來 174 個已合併 PR、581 個 commit，554 個檔案變動（+24,012 / −3,144）"
  - "新增 Group Chats 的 opt-in lead routing，且 cron 任務可發文至群聊"
  - "完整版 release notes 將隨 v0.23.0 發布"
tags: [hermes-agent, patch-release, release-notes]
topics: [agents.frameworks]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.22.7

Hermes Agent v0.22.7 是整合約 174 個已合併 PR 的補丁版本。

**What** 同步發布於 GitHub（CLI 與安裝程式）、Microsoft Store、Docker 與 Hermes Cloud；另有群聊 lead routing、Kanban 釘選看板、Telegram 接入 Team Gateway 等未在本版文件化的功能，完整說明待 v0.23.0。

### 重點
- 彙整 v0.22.6 以來 174 個已合併 PR、581 個 commit，554 個檔案變動（+24,012 / −3,144）
- 新增 Group Chats 的 opt-in lead routing，且 cron 任務可發文至群聊
- 完整版 release notes 將隨 v0.23.0 發布

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.22.7 
 Release Date: November 3, 2026 
 
 Patch release. This tag rolls up the ~174 PRs merged since v0.22.6 into a stable release for the GitHub release (CLI and installers), the Microsoft Store app, Docker and Hermes Cloud. Full curated notes for this window ship with v0.23.0. 
 

 About this release 
 Measured at commit b200f5bc60e , the window since v0.22.6 contains 581 non-merge commits across 554 changed files (+24,012 / −3,144), 174 merged PRs and 29 closed issues . 
 Also in the window, undocumented here on purpose: opt-in lead routing for Desktop Group Chats (with a Lead badge on the room header), cron jobs that post into Group Chats, room purpose and shared notes, group rooms laid out in one chat column with each member's live state, pinned Kanban boards as quick-switch tabs, $$TeX$$ diagram labels and mermaid diagrams rendered through Pele, a Desktop update error box that shows the failed update's output with a report link, Web Access naming the step Start is on with a running clock, Telegram on Team Gateway set up by linking an account to the shared bot, an opt-in Slack thread_followup_silence for unaddressed thread replies, a Daybreak switch for catalog-listed ChatGPT subscription models, and a batch of new plugin-catalog entries. 
 Full curated release notes for this window ship with v0.23.0 , which will document everything from v0.22.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.22.6...v0.22.7

</details>