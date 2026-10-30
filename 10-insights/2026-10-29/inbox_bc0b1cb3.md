---
id: inbox_bc0b1cb3
date: 2026-10-29
source_ref: "[[00-inbox/2026-10-29/0035-claude-mem-releases-v15-6-0-810a]]"
title: "v15.6.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.6.0
source: claude-mem-releases
published_at: 2026-10-29T17:01:29+00:00
fetched_at: 2026-10-30T00:43:29.390945+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v15.6.0 將 My Work 檢視器的狀態統一到單一 Zustand store。 **Why** 原本狀態分散在模組 store、App 元件狀態與 React context 三處。 **How** 拆為 work、view、rules、focus 四個 slice，並以 ?view=、?focus=、?request= 參數把頁面狀態寫進 URL。 **What** 重新整理與上下頁可保留狀態，列表篩選與排序會記住；My Rules 一次只允許一筆儲存，規則變更後 Undo 會被拒絕。"
key_points:
  - "狀態由三處合併為一個 Zustand store，拆為 work/view/rules/focus 四個 slice（#5187）"
  - "URL 參數 ?view=、?focus=、?request= 保存頁面狀態，支援重新載入與上一頁/下一頁"
  - "My Rules 一次只允許一筆儲存；Approve/Reject 收據綁定儲存時的版本，規則變動後 Undo 被拒絕"
tags: [claude-mem, zustand, state-management, release-notes]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.6.0

claude-mem v15.6.0 將 My Work 檢視器的狀態統一到單一 Zustand store。

**Why** 原本狀態分散在模組 store、App 元件狀態與 React context 三處。

**How** 拆為 work、view、rules、focus 四個 slice，並以 ?view=、?focus=、?request= 參數把頁面狀態寫進 URL。

**What** 重新整理與上下頁可保留狀態，列表篩選與排序會記住；My Rules 一次只允許一筆儲存，規則變更後 Undo 會被拒絕。

### 重點
- 狀態由三處合併為一個 Zustand store，拆為 work/view/rules/focus 四個 slice（#5187）
- URL 參數 ?view=、?focus=、?request= 保存頁面狀態，支援重新載入與上一頁/下一頁
- My Rules 一次只允許一筆儲存；Approve/Reject 收據綁定儲存時的版本，規則變動後 Undo 被拒絕

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.6.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

My Work: one store for the viewer's state ( #5187 ) 
 My Work used to keep its state in three places: a hand-rolled module store, component state in App , and React contexts. It now runs on one Zustand store split into four slices: work, view, rules and focus. 
 What you'll notice 
 
 Reload and Back/Forward work. The page, focus area and open request drawer are in the URL ( ?view= , ?focus= , ?request= ). 
 Your list view, filter and sort are remembered between visits. The theme still follows your system or ?theme= . If browser storage is blocked, preferences last for the current visit only. 
 Live updates are steadier. A stopped source can't publish. An older read never overwrites a newer live model. When a live update overtakes a save, you see the current model and your save is kept. Heartbeats re-render only the status indicators. 
 The drawer follows its request by id and closes when the request leaves the feed. If the first read fails, you get a Retry button. A selected Closed filter stays visible even when nothing matches. 
 My Rules: one save at a time, with controls disabled while a save runs. Each Approve/Reject receipt is tied to the version the worker saved, and Undo is refused once the rule has changed since. 
 My Focus: all screens share one save history. 
 
 Worker 
 
 Rule saves return savedRuleId . 
 "Load in Claude Code" publishes the change to other open tabs. 
 The feed signature includes rulesFile . 
 
 Full changelog: v15.5.0...v15.6.0

</details>