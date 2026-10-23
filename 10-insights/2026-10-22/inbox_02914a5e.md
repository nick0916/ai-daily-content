---
id: inbox_02914a5e
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-ruflo-releases-v3-59-14-explicit-memory-store-targeting-4c55]]"
title: "v3.59.14 — explicit memory-store targeting + workflow_list total-count fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.14
source: ruflo-releases
published_at: 2026-10-22T04:43:10+00:00
fetched_at: 2026-10-23T01:01:19.148811+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "RuFlo 讓 memory 工具可指定儲存路徑，並修正 workflow_list 的 total 計數。 **Why** 選擇特定 store 時不應強制觸發預設 store 的初始化與遷移；*_list 工具的 total 若在分頁切片後計算，會永遠等於頁面大小。 **How** memory_store、memory_retrieve、memory_search（含 SmartRetrieval 的 raw search 與 near-miss 路徑）、memory_delete、memory_list 新增可選 dbPath 參數；workflow_list 的 total 改在 .slice(0, limit) 之前計算。 **What** 對應 PR #3196、#4350、#4372，並附帶 #4369 讓 ruflo-browser 的 smoke.sh 在 monorepo 外跳過 CLI 原始碼檢查；mcp-memory 測試 4 項與 workflow-list 測試 3 項通過。"
key_points:
  - "memory_store、memory_retrieve、memory_search、memory_delete、memory_list 新增可選 dbPath，指定 store 時不再強制初始化或遷移預設 store（#3196、#4350）"
  - "workflow_list 的 total 改為在 slice 之前計算，反映真實符合數（#4372）"
  - "原文將此列為 *_list MCP 工具同類 bug 的第 6 次出現，建議做一次專門審計"
tags: [mcp-tools, memory-store, pagination-bug, ruflo]
topics: [agents.frameworks]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.14 — explicit memory-store targeting + workflow_list total-count fix

RuFlo 讓 memory 工具可指定儲存路徑，並修正 workflow_list 的 total 計數。 **Why** 選擇特定 store 時不應強制觸發預設 store 的初始化與遷移；*_list 工具的 total 若在分頁切片後計算，會永遠等於頁面大小。 **How** memory_store、memory_retrieve、memory_search（含 SmartRetrieval 的 raw search 與 near-miss 路徑）、memory_delete、memory_list 新增可選 dbPath 參數；workflow_list 的 total 改在 .slice(0, limit) 之前計算。 **What** 對應 PR #3196、#4350、#4372，並附帶 #4369 讓 ruflo-browser 的 smoke.sh 在 monorepo 外跳過 CLI 原始碼檢查；mcp-memory 測試 4 項與 workflow-list 測試 3 項通過。

### 重點
- memory_store、memory_retrieve、memory_search、memory_delete、memory_list 新增可選 dbPath，指定 store 時不再強制初始化或遷移預設 store（#3196、#4350）
- workflow_list 的 total 改為在 slice 之前計算，反映真實符合數（#4372）
- 原文將此列為 *_list MCP 工具同類 bug 的第 6 次出現，建議做一次專門審計

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.14)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 
 fix(mcp): let memory tools target an explicit store ( #3196 , #4350 ) — memory_store , memory_retrieve , memory_search (including SmartRetrieval's raw search and near-miss paths), memory_delete , and memory_list now accept an optional dbPath . Selecting an explicit store no longer forces default-store initialization/migration. 
 fix(mcp): report every stored workflow in workflow_list 's total , not just the limited page ( #4372 ) — total is now computed before .slice(0, limit) cuts the page, matching the real match count instead of always equaling the page size. 6th instance of this bug class across *_list MCP tools (after task_list , session_list , claims_list , others) — worth a dedicated audit pass. 
 fix(ruflo-browser): skip CLI source check outside the monorepo ( #4369 , issue #2912 ) — smoke.sh 's lifecycle-tools check now matches the same SKIP convention already used by ruflo-console 's smoke script when the monorepo CLI source isn't beside the plugin. 
 
 Verification 
 
 mcp-memory-explicit-dbpath-3196.test.ts (4 tests), workflow-list-total.test.ts (3 tests): both passing against the built package. 
 audit-umbrella-version-lockstep.mjs and audit-leaf-versions-published.mjs : both clean. 
 All three source PRs went fully green in CI independently before merge. 
 Witness verify (signed manifest) jobs green on linux/macos/windows after a same-day follow-up fix ( #4374 ) corrected a self-inflicted history.jsonl false-regression from an unbuilt-checkout regen.mjs --history run — see that PR for the correction. 
 
 🤖 Generated with RuFlo

</details>