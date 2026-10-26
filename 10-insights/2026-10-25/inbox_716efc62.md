---
id: inbox_716efc62
date: 2026-10-25
source_ref: "[[00-inbox/2026-10-25/0250-claude-mem-releases-v15-2-0-browser-install-funnel-1824]]"
title: "v15.2.0 — Browser install funnel"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.2.0
source: claude-mem-releases
published_at: 2026-10-25T11:52:16+00:00
fetched_at: 2026-10-26T02:58:59.316043+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 新增瀏覽器安裝流程，把近期工作整理成 Work、Goals 與 Rules。 **How** 掃描近 30 天本地 agent 歷史，過濾後以 gzip 上傳 CMEM Cloud 做雲端意圖抽取。 **What** 提供 At Home 與 On The Go 兩種儲存選項；雲端漏分組的對話保留為未決定並獨立顯示，不再讓設定失敗。需 Node ^20.19.0 或 >=22.12.0。"
key_points:
  - "npx claude-mem install 會安裝 hooks、啟動 worker 並開啟瀏覽器設定流程"
  - "Cloud 漏分組的對話保留為 undecided，顯示為獨立請求，不再讓 setup 失敗"
  - "Ongoing refresh 依賴已安裝並登入的 agent（Claude Code、Codex、Gemini）"
tags: [claude-mem, agent-memory, privacy, install-flow, llm-extraction]
topics: [agents.coding_agents, security]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.2.0 — Browser install funnel

claude-mem 新增瀏覽器安裝流程，把近期工作整理成 Work、Goals 與 Rules。 **How** 掃描近 30 天本地 agent 歷史，過濾後以 gzip 上傳 CMEM Cloud 做雲端意圖抽取。 **What** 提供 At Home 與 On The Go 兩種儲存選項；雲端漏分組的對話保留為未決定並獨立顯示，不再讓設定失敗。需 Node ^20.19.0 或 >=22.12.0。

### 重點
- npx claude-mem install 會安裝 hooks、啟動 worker 並開啟瀏覽器設定流程
- Cloud 漏分組的對話保留為 undecided，顯示為獨立請求，不再讓 setup 失敗
- Ongoing refresh 依賴已安裝並登入的 agent（Claude Code、Codex、Gemini）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.2.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Highlights 
 Install funnel in the browser ( #5031 ) 
 Fresh installs now open a browser setup flow that finds your recent work and turns it into Work, Goals and Rules before setup finishes. Existing installations keep opening My Work as before. 
 
 Install — npx claude-mem install installs the detected hooks, starts the worker and opens the browser. 
 Scan — reads the last 30 days of supported local agent history. Configured excluded projects and agent-authored prompts are left out, stored prompts are deduplicated, and private-tag cleanup and configured redaction run before anything is shown or extracted. 
 Reveal — uploads the filtered owner prompts (gzip) to CMEM Cloud for hosted intent extraction. Anonymous installs get a private, persistent installation credential that retries and sign-in reuse. Returned goals, rules and request groups fill the local My Work snapshots. Upload and extraction errors are shown and can be retried. The pre-checked product-improvement box only changes improveProduct . 
 Storage choice — At Home or On The Go. On The Go uses the existing pairing, login and checkout flow; delivered memory credentials are activated before checkout is marked paid, and sync-only accounts keep their provider. 
 Finish Setup — installs any other selected local tools and can import existing memory. Extraction or import in progress is kept when a settings change restarts the worker. 
 What's next — search saved memory and prompts, keep a result as a note, then hand off to My Work. The terminal exits successfully. 
 
 Ongoing goals and progress refresh uses an installed, logged-in agent: Claude Code gets bounded file tools and memory recall only; Codex runs with a strict read-only workspace/runtime profile (no writes, no network), with native and npm runtime layouts supported; Gemini gets prepared evidence inline with no builtin tools, hooks or YOLO mode. Every saved answer passes the worker's validators. 
 Setup no longer fails when Cloud leaves conversations ungrouped ( #5060 ) 
 On real 30-day scans the hosted model sometimes leaves conversations out of every group. The worker used to throw Hosted extraction omitted conversation ... and fail setup after a successful hosted run. Now the groups Cloud returned are saved and conversations it did not place stay undecided: they show in My Work as their own request, and the local refresh can group them later. Unknown or repeated conversation ids still fail loudly. 
 Requirements 
 
 Node ^20.19.0 || &gt;=22.12.0 . 
 Uses CMEM Cloud hosted history import and intent extraction (claude-mem-pro #353 , #355 , #358 ). 
 
 Full Changelog : v15.1.0...v15.2.0

</details>