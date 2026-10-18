---
id: inbox_2818bbd7
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-claude-mem-releases-v13-41-0-45c7]]"
title: "v13.41.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.41.0
source: claude-mem-releases
published_at: 2026-10-17T02:17:07+00:00
fetched_at: 2026-10-18T03:20:52.723897+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude-Mem v13.41.0 新增 workflow skills 與 work-state 遙測。Workflow skills：build 透過 make-plan、do、babysit 委派一個 coding session；release 透過 version-bump 與 childhood 委派發布；build-and-release 兩者皆跑，並在 PR 就緒後合併，再從更新後的 main 繼續。同時恢復既有的 childhood skill，使發布後驗證包含在內。遙測方面，新增以 PostHog 為基礎、保護隱私的 work-state 使用彙總，依 release、host platform、記錄的 agent role 分組，區分 captured reads/writes、outcomes、native to-do 使用、instruction handoffs 與缺少歸屬的情況。MCP execution receipts 涵蓋 worker 回應前的失敗，屬獨立觀測來源，不可加進 captured-call 總數。官方明確表示這些是診斷訊號而非合規分數：回傳指令不代表 host 接受或 agent 遵循，一般提問也可能合理地不需寫入。不會傳送任務標題、prompt 文字、專案路徑或原始 session/agent ID，既有的遙測 opt-out 仍有效，且不回補過去的使用資料。"
key_points:
  - "新增 build、release、build-and-release 三個薄包裝 skill，重用 make-plan／do／babysit 與 version-bump／childhood 既有流程"
  - "遙測隱私設計：不傳任務標題、prompt 文字、專案路徑、原始 session/agent ID；沿用既有 opt-out；本地 replay 去重保留 30 天，更舊事件丟棄"
  - "指標詮釋原則：instruction handoff 只在平台 adapter 格式化後且 stdout 成功才計入，且僅為診斷訊號，不證明 agent 有遵循指令"
tags: [claude-mem, telemetry, posthog, workflow-skills, privacy]
topics: [agents.coding_agents, product_and_org.product]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.41.0

Claude-Mem v13.41.0 新增 workflow skills 與 work-state 遙測。Workflow skills：build 透過 make-plan、do、babysit 委派一個 coding session；release 透過 version-bump 與 childhood 委派發布；build-and-release 兩者皆跑，並在 PR 就緒後合併，再從更新後的 main 繼續。同時恢復既有的 childhood skill，使發布後驗證包含在內。遙測方面，新增以 PostHog 為基礎、保護隱私的 work-state 使用彙總，依 release、host platform、記錄的 agent role 分組，區分 captured reads/writes、outcomes、native to-do 使用、instruction handoffs 與缺少歸屬的情況。MCP execution receipts 涵蓋 worker 回應前的失敗，屬獨立觀測來源，不可加進 captured-call 總數。官方明確表示這些是診斷訊號而非合規分數：回傳指令不代表 host 接受或 agent 遵循，一般提問也可能合理地不需寫入。不會傳送任務標題、prompt 文字、專案路徑或原始 session/agent ID，既有的遙測 opt-out 仍有效，且不回補過去的使用資料。

### 重點
- 新增 build、release、build-and-release 三個薄包裝 skill，重用 make-plan／do／babysit 與 version-bump／childhood 既有流程
- 遙測隱私設計：不傳任務標題、prompt 文字、專案路徑、原始 session/agent ID；沿用既有 opt-out；本地 replay 去重保留 30 天，更舊事件丟棄
- 指標詮釋原則：instruction handoff 只在平台 adapter 格式化後且 stdout 成功才計入，且僅為診斷訊號，不證明 agent 有遵循指令

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.41.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Build, release, and work-state visibility 
 Workflow skills 
 
 build delegates a coding session through make-plan , do , and babysit . 
 release delegates publication through version-bump and childhood . 
 build-and-release runs both, merging the ready PR before continuing from updated main. 
 Restores the existing childhood skill so post-release verification is included. 
 
 The new wrappers are deliberately short. They reuse the existing workflows. 
 Work-state telemetry 
 Adds privacy-preserving PostHog rollups for work-state usage by release, host platform, and recorded agent role. The rollups distinguish captured reads and writes, outcomes, native to-do use, instruction handoffs, and missing attribution. 
 MCP execution receipts also cover failures before a worker responds. They are a separate observation source and must not be added to captured-call totals. 
 Instruction handoffs are measured after the platform adapter formats the model-bound output and stdout succeeds. Cached context is included; discarded context and failed output are not counted as successful handoffs. Delayed or untimestamped captures cannot inherit a later instruction handoff. 
 These are diagnostic signals, not a compliance score. Returning instructions does not prove that a host accepted them or an agent followed them, and an ordinary question may correctly require no write. 
 No task titles, prompt text, project paths, or raw session/agent IDs are sent. Existing telemetry opt-out remains in effect. This release does not backfill earlier usage. 
 Local replay deduplication lasts 30 days; older events are dropped. Public/private turn boundaries remain content-free and prevent private activity from inheriting an earlier public prompt. Hosts without verified original timestamps remain outside captured prompt/tool totals.

</details>