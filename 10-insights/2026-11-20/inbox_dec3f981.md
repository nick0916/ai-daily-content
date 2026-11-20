---
id: inbox_dec3f981
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0105-hermes-agent-releases-hermes-agent-v0-23-3-6749]]"
title: "Hermes Agent v0.23.3"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.3
source: hermes-agent-releases
published_at: 2026-11-20T00:34:38+00:00
fetched_at: 2026-11-20T01:13:59.990288+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 發布 v0.23.3 修補版，彙整 v0.23.2 以來約 370 個 PR。 **Why** 這個版本把大量變更整合成穩定版，供 CLI、桌面 app、Microsoft Store、Docker 與 Hermes Cloud 使用。 **What** 期間共 1,657 個非 merge commits 與 60 個已關閉 issues；新增 prompt cache 生命週期控制（預設 cache_ttl 為 auto），並讓 GPT-6.2 Astra 與 Sol（含 Pro）上線 OpenRouter 與 Nous Portal。完整說明將於 v0.24.0 提供。"
key_points:
  - "v0.23.3 彙整約 370 個 PR，共 1,657 個非 merge commits、3,948 個變更檔案"
  - "新增 prompt cache 生命週期控制，閒置對話在 1 小時快取過期前壓縮，預設 cache_ttl 為 auto"
  - "GPT-6.2 Astra 與 Sol（含 Pro）上線 OpenRouter 與 Nous Portal；完整發布說明將於 v0.24.0 提供"
tags: [hermes-agent, prompt-caching, release-notes, openrouter, nous-portal]
topics: [agents.frameworks, engineering.inference]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.23.3

Hermes Agent 發布 v0.23.3 修補版，彙整 v0.23.2 以來約 370 個 PR。

**Why** 這個版本把大量變更整合成穩定版，供 CLI、桌面 app、Microsoft Store、Docker 與 Hermes Cloud 使用。

**What** 期間共 1,657 個非 merge commits 與 60 個已關閉 issues；新增 prompt cache 生命週期控制（預設 cache_ttl 為 auto），並讓 GPT-6.2 Astra 與 Sol（含 Pro）上線 OpenRouter 與 Nous Portal。完整說明將於 v0.24.0 提供。

### 重點
- v0.23.3 彙整約 370 個 PR，共 1,657 個非 merge commits、3,948 個變更檔案
- 新增 prompt cache 生命週期控制，閒置對話在 1 小時快取過期前壓縮，預設 cache_ttl 為 auto
- GPT-6.2 Astra 與 Sol（含 Pro）上線 OpenRouter 與 Nous Portal；完整發布說明將於 v0.24.0 提供

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.23.3 
 Release Date: November 19, 2026 
 
 Patch release. This tag rolls up the ~370 PRs merged since v0.23.2 into a stable release for the GitHub release (CLI and installers), the Microsoft Store app, Docker and Hermes Cloud. Full curated notes for this window ship with v0.24.0. 
 

 About this release 
 Measured at commit caafe5389ae , the window since v0.23.2 contains 1,657 non-merge commits across 3,948 changed files (+222,379 / −96,154), 370 merged PRs and 60 closed issues . 
 Also in the window, undocumented here on purpose: one prompt-cache lifecycle controller (warming through long tool runs, compaction of idle chats before the 1h cache expires, Nous Portal on the full 1h lifecycle, prompt_caching.cache_ttl defaulting to auto ), compaction that archives the tool results it drops, the proactive tool-result prune on by default, a one-question first-run CLI setup with the free tier included, GPT-6.2 Astra and Sol (+ Pro) on OpenRouter and Nous Portal, a "Waiting on teammates" strip above Bot Chat composers, the Linux AppImage agent payload run from a stable per-build copy, the storage layer split behind a persistence interface with its SQLite backend, dependency security bumps (oauthlib, opentelemetry, tornado), and a large batch of new plugin-catalog entries. 
 Full curated release notes for this window ship with v0.24.0 , which will document everything from v0.23.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.23.2...v0.23.3

</details>