---
id: inbox_ee0f99fa
date: 2026-11-10
source_ref: "[[00-inbox/.../inbox_ee0f99fa]]"
title: "Hermes Agent v0.23.1"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.1
source: hermes-agent-releases
published_at: 2026-11-10T01:42:15+00:00
fetched_at: 2026-11-10T23:36:56.557907+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent v0.23.1 修正外掛目錄超過大小上限、安裝時退回舊清單的問題。 **Why** 外掛目錄 JSON 超過客戶端 2 MiB 上限後，安裝會靜默退回隨版本附帶的舊目錄，新外掛與移除項目都無法反映。 **How** 將上限提高到 16 MiB，線上目錄重新生效。 **What** 2026-11-09 發布的修補版本，彙整 v0.23.0 以來約 618 個合併 PR；CLI、Microsoft Store、Docker 皆更新，完整發行說明將隨 v0.24.0 提供；v0.23.0 以前的版本需更新才會修正。"
key_points:
  - "plugin-catalog.json 超過 2 MiB 上限後，hermes plugins install 靜默使用內建舊目錄"
  - "修正方式：上限提高至 16 MiB（PR #151860，修 issue #151856）"
  - "v0.23.0 以前的版本需更新才會生效；完整說明待 v0.24.0"
tags: [hermes-agent, plugin-catalog, patch-release, silent-fallback, nous-research]
topics: [agents.frameworks]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.23.1

Hermes Agent v0.23.1 修正外掛目錄超過大小上限、安裝時退回舊清單的問題。

**Why** 外掛目錄 JSON 超過客戶端 2 MiB 上限後，安裝會靜默退回隨版本附帶的舊目錄，新外掛與移除項目都無法反映。

**How** 將上限提高到 16 MiB，線上目錄重新生效。

**What** 2026-11-09 發布的修補版本，彙整 v0.23.0 以來約 618 個合併 PR；CLI、Microsoft Store、Docker 皆更新，完整發行說明將隨 v0.24.0 提供；v0.23.0 以前的版本需更新才會修正。

### 重點
- plugin-catalog.json 超過 2 MiB 上限後，hermes plugins install 靜默使用內建舊目錄
- 修正方式：上限提高至 16 MiB（PR #151860，修 issue #151856）
- v0.23.0 以前的版本需更新才會生效；完整說明待 v0.24.0

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Hermes Agent v0.23.1

Hermes Agent v0.23.1 
 Release Date: November 9, 2026 
 
 Patch release. This tag rolls up the ~618 PRs merged since v0.23.0 into a stable release for the GitHub release (CLI and installers), the Microsoft Store app, Docker and Hermes Cloud. Full curated notes for this window ship with v0.24.0. 
 
 What this patch ships for plugin users: since the plugin catalog's site deploy on November 9, the published plugin-catalog.json was larger than the 2 MiB cap clients accept, so every install silently fell back to the catalog it shipped with. hermes plugins install could not find plugins added since your last update, installed the pin your release shipped instead of the current one, and missed newer removed entries. This release raises the cap to 16 MiB, so the live catalog is used again ( #151860 , fixes #151856 , thanks @100yenadmin ). Installs that stay on v0.23.0 or older keep falling back until they update. 

 About this release 
 Measured at commit 3b421578588 , the window since v0.23.0 contains 2,578 non-merge commits across 2,781 changed files (+151,690 / −62,595), 618 merged PRs and 409 closed issues . 
 Also in the window, undocumented here on purpose: Esc backtrack in the TUI and classic CLI (replacing the rewind list picker), group chats that run on a gateway without Desktop and can seat bots from other computers, saved gateway connections shared by Desktop and the Webapp, signing the in-app browser in with your real browser profile and filling saved logins from its address bar, hermes gateway attach for local clients, hermes clipboard image --json , new plugin API (session-scoped environment values, plugin JSON-RPC methods and events, llm.oneshot auxiliary tasks, a compression-stable conversation_id , an on_session_open hook in the gateway, a post_curator_run hook), faster transcript and handoff reads, and a large batch of new plugin-catalog entries. 
 Full curated release notes for this window ship with v0.24.0 , which will document everything from v0.23.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.23.0...v0.23.1

</details>