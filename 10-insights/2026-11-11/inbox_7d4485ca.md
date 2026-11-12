---
id: inbox_7d4485ca
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-codex-releases-0-167-2-8c8a]]"
title: "0.167.2"
url: https://github.com/openai/codex/releases/tag/rust-v0.167.2
source: codex-releases
published_at: 2026-11-11T22:46:17+00:00
fetched_at: 2026-11-12T02:57:57.568325+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex 在 Google Cloud Vertex AI 上改為預設以增量方式傳送工具更新。 **What** OpenAI Codex 0.167.2 讓 Vertex AI 預設以增量方式傳送 tool updates；若要沿用舊行為，在 config.toml 的 [features] 下設 incremental_tools_legacy_gcp = false。相關 PR 為 #60617、#60848。"
key_points:
  - "OpenAI Codex 0.167.2：Google Cloud Vertex AI 預設增量傳送工具更新"
  - "退出方式：config.toml 的 [features] 設 incremental_tools_legacy_gcp = false"
  - "相關 PR：#60617、#60848"
tags: [openai-codex, vertex-ai, release, config]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.167.2

OpenAI Codex 在 Google Cloud Vertex AI 上改為預設以增量方式傳送工具更新。

**What** OpenAI Codex 0.167.2 讓 Vertex AI 預設以增量方式傳送 tool updates；若要沿用舊行為，在 config.toml 的 [features] 下設 incremental_tools_legacy_gcp = false。相關 PR 為 #60617、#60848。

### 重點
- OpenAI Codex 0.167.2：Google Cloud Vertex AI 預設增量傳送工具更新
- 退出方式：config.toml 的 [features] 設 incremental_tools_legacy_gcp = false
- 相關 PR：#60617、#60848

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.167.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New Features 
 
 Codex now sends tool updates incrementally by default on Google Cloud Vertex AI. To opt out, set incremental_tools_legacy_gcp = false under [features] in config.toml . ( #60617 , #60848 ) 
 
 Changelog 
 Full Changelog: rust-v0.167.1...rust-v0.167.2

</details>