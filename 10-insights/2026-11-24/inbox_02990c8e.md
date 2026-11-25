---
id: inbox_02990c8e
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0007-hermes-agent-releases-hermes-agent-v0-23-4-42ea]]"
title: "Hermes Agent v0.23.4"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.4
source: hermes-agent-releases
published_at: 2026-11-24T08:17:06+00:00
fetched_at: 2026-11-25T00:14:52.882010+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent 發布 v0.23.4 修補版，把 v0.23.3 之後約 229 個 PR 打包成穩定版。 **What** 發布於 2026-11-23，涵蓋 GitHub 發布版（CLI 與安裝程式）、Microsoft Store、Docker 與 Hermes Cloud；該期間共 1,122 個非 merge commit、1,316 個檔案變更（+96,873 / −6,703）、281 個已關閉 issue。完整說明將隨 v0.24.0 提供。"
key_points:
  - "該期間共 1,122 個非 merge commit、1,316 個檔案變更（+96,873 / −6,703）、281 個已關閉 issue"
  - "原文提及但未逐項說明：Gemini 4 Hydrogen、Neon、Carbon 上線於 Nous Portal、OpenRouter、Vertex"
  - "新增 hermes gateway migrate --backends 與 hermes plugins config 等指令"
tags: [hermes-agent, release, nous-research, patch-release]
topics: [agents.frameworks]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.23.4

Hermes Agent 發布 v0.23.4 修補版，把 v0.23.3 之後約 229 個 PR 打包成穩定版。

**What** 發布於 2026-11-23，涵蓋 GitHub 發布版（CLI 與安裝程式）、Microsoft Store、Docker 與 Hermes Cloud；該期間共 1,122 個非 merge commit、1,316 個檔案變更（+96,873 / −6,703）、281 個已關閉 issue。完整說明將隨 v0.24.0 提供。

### 重點
- 該期間共 1,122 個非 merge commit、1,316 個檔案變更（+96,873 / −6,703）、281 個已關閉 issue
- 原文提及但未逐項說明：Gemini 4 Hydrogen、Neon、Carbon 上線於 Nous Portal、OpenRouter、Vertex
- 新增 hermes gateway migrate --backends 與 hermes plugins config 等指令

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.23.4 
 Release Date: November 23, 2026 
 
 Patch release. This tag rolls up the ~229 PRs merged since v0.23.3 into a stable release for the GitHub release (CLI and installers), the Microsoft Store app, Docker and Hermes Cloud. Full curated notes for this window ship with v0.24.0. 
 

 About this release 
 Measured at commit 8fc03744473 , the window since v0.23.3 contains 1,122 non-merge commits across 1,316 changed files (+96,873 / −6,703), 229 merged PRs and 281 closed issues . 
 Also in the window, undocumented here on purpose: Gemini 4 Hydrogen, Neon and Carbon on Nous Portal, OpenRouter and Vertex, hermes gateway migrate --backends to move an old serve/dashboard backend onto the gateway (with a System page card in the dashboard), hermes plugins config to edit a plugin's settings from the terminal, approval cards in Desktop for a sandbox's folder and site requests, gateway clients announcing who they are so plugins can see which client sent a turn, a long run of Desktop streaming and transcript performance work, a retryable indicator for slow profile switches, hermes dashboard password without a TTY prompt, configurable skill index description length ( skills.index_desc_limit ), managed-scope config honored by security and URL-safety reads, and a large batch of new plugin-catalog entries. 
 Full curated release notes for this window ship with v0.24.0 , which will document everything from v0.23.0 onward — highlights, feature areas, and complete contributor credits. Nothing in this window is skipped. 
 Updating 
 
 Microsoft Store app: updates through the Store. 
 Desktop app installed from the installer (.exe / .dmg): no change in this release; it updates with the next bundled release. 
 CLI: hermes update , or re-run the installer one-liner. 
 Docker / Hermes Cloud: nousresearch/hermes-agent:stable (or :latest ). 
 
 Full Changelog : v0.23.3...v0.23.4

</details>