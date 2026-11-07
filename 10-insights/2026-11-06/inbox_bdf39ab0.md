---
id: inbox_bdf39ab0
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-claude-mem-releases-v15-11-0-6abf]]"
title: "v15.11.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.11.0
source: claude-mem-releases
published_at: 2026-11-06T22:17:48+00:00
fetched_at: 2026-11-07T01:49:29.432323+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v15.11.0 新增安裝流程的畫面遙測，並修正背景 worker 在配額或認證恢復後重播過期工作的問題。 **How** 安裝畫面只記錄進入、返回與完成等事件，不含提示詞、檔名、URL 或憑證；待處理的觀察輸入 5 分鐘後過期，配額或認證失敗時丟棄。 **What** 安裝流程共 9 個畫面（Scan 至 Workspace）；Server viewer 讀取端點恢復；Windows 預設 worker port 改為依安裝separately 計算。完整比較為 v15.10.1...v15.11.0。"
key_points:
  - "待處理的觀察輸入 5 分鐘過期，配額或認證失敗時丟棄，避免恢復後重播舊工作"
  - "安裝流程追蹤 9 個畫面，遙測事件遵循 DO_NOT_TRACK 設定，並排除提示詞與憑證"
  - "Server viewer 讀取端點恢復，沿用既有 team/project 授權"
tags: [claude-mem, telemetry, worker-queue, memory, observability]
topics: [agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.11.0

claude-mem v15.11.0 新增安裝流程的畫面遙測，並修正背景 worker 在配額或認證恢復後重播過期工作的問題。

**How** 安裝畫面只記錄進入、返回與完成等事件，不含提示詞、檔名、URL 或憑證；待處理的觀察輸入 5 分鐘後過期，配額或認證失敗時丟棄。

**What** 安裝流程共 9 個畫面（Scan 至 Workspace）；Server viewer 讀取端點恢復；Windows 預設 worker port 改為依安裝separately 計算。完整比較為 v15.10.1...v15.11.0。

### 重點
- 待處理的觀察輸入 5 分鐘過期，配額或認證失敗時丟棄，避免恢復後重播舊工作
- 安裝流程追蹤 9 個畫面，遙測事件遵循 DO_NOT_TRACK 設定，並排除提示詞與憑證
- Server viewer 讀取端點恢復，沿用既有 team/project 授權

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.11.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Installer screen telemetry and runtime fixes 
 Claude-Mem now records progress through the local setup screens, so the admin can show where setup continues, goes back, encounters a known error, or has no recorded next step. 
 
 Track the nine actual setup screens: Scan, Reveal, Choose memory, Review savings, Checkout, Finish setup, Import history, Launch, and Workspace. 
 Count each rendered screen visit separately. Returning to a screen creates a new visit; failed hand-offs do not become successful forward transitions. 
 Preserve the real setup branches. At Home and existing Pro configurations skip checkout, history import returns to Finish setup, and reduced-motion setup skips the launch animation. 
 Record local setup completion only after the worker accepts the successful setup state write. 
 Preserve pending screen events when setup finishes and retry temporary local-worker connection failures, so a fast completion or a slow telemetry request does not lose the visit history. 
 Pass a fresh setup-attempt ID through the existing installer pairing when telemetry is enabled, allowing the matching admin report to connect setup progress to the authorized account flow. 
 
 The events follow the existing analytics settings, including DO_NOT_TRACK . Their schema accepts only known screen IDs, actions, error codes, timestamps, and random attempt/visit IDs. Prompts, filenames, URLs, credentials, and free-form error text are excluded. Sample previews do not emit setup events. The worker's long-lived anonymous identity is not aliased to an account. 
 Per-screen history starts with this release. Older installers did not record these screens, so their missing events are not treated as zero conversions or abandonment. 
 Runtime fixes included since v15.10.1 
 
 Stop replaying stale local observer work after quota or authentication recovery. Live capture uses a bounded handoff; pending inputs expire after five minutes and are discarded on quota/authentication failure. Saved memories and original transcripts remain intact. Capture skipped during an outage is not automatically backfilled. 
 Restore the server viewer's read endpoints using the server's Postgres data and existing team/project authorization. Shared server log files remain unavailable to tenant keys. 
 Stop advertising dumb_search on the server runtime, where only the local worker can execute it. 
 Derive the default worker port per installation to avoid local port collisions while preserving the legacy Windows server port. 
 Show files outside a project under the home directory as ~/... in generated context, rather than long chains of parent-directory segments. 
 Prefer the configured provider's agent for My Work refreshes. 
 
 Full comparison: v15.10.1...v15.11.0

</details>