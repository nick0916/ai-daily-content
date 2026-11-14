---
id: inbox_c294cea8
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/0146-claude-mem-releases-v15-18-2-e124]]"
title: "v15.18.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.18.2
source: claude-mem-releases
published_at: 2026-11-12T17:40:57+00:00
fetched_at: 2026-11-14T01:56:16.151988+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 修正 Windows 上 Gemini CLI hook 自 15.18.0 起全數失敗的問題。 **Why** Gemini 的 hook 透過 PowerShell 執行，命令以引號路徑開頭被判為解析錯誤，每個事件都失敗，Windows 上的 session 因此未被儲存。 **How** Windows 上 hook 命令改以 PowerShell 的 & 呼叫運算子開頭，與 Cursor、Windsurf 既有做法相同。 **What** Windows 的 Gemini CLI 使用者需執行一次 npx claude-mem gemini install，update 與自動更新不會改寫舊 hook；另 My Work 改以模型判讀開放工作狀態，信心 0.8 以上才顯示判定結果，標籤存於 work-view/work-state-labels.json。"
key_points:
  - "Windows 上 Gemini hook 自 15.18.0 起每個事件都因 PowerShell 解析錯誤失敗；改用 & 呼叫運算子"
  - "Windows 使用者需執行一次 npx claude-mem gemini install；update 與自動更新不會重寫 hook"
  - "My Work 以模型判讀 open work-state，信心 ≥0.8 才取代過時狀態；標籤存於 work-view/work-state-labels.json，原始 log 不寫入"
tags: [claude-mem, gemini-cli, windows, powershell, my-work]
topics: [agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.18.2

claude-mem 修正 Windows 上 Gemini CLI hook 自 15.18.0 起全數失敗的問題。

**Why** Gemini 的 hook 透過 PowerShell 執行，命令以引號路徑開頭被判為解析錯誤，每個事件都失敗，Windows 上的 session 因此未被儲存。

**How** Windows 上 hook 命令改以 PowerShell 的 & 呼叫運算子開頭，與 Cursor、Windsurf 既有做法相同。

**What** Windows 的 Gemini CLI 使用者需執行一次 npx claude-mem gemini install，update 與自動更新不會改寫舊 hook；另 My Work 改以模型判讀開放工作狀態，信心 0.8 以上才顯示判定結果，標籤存於 work-view/work-state-labels.json。

### 重點
- Windows 上 Gemini hook 自 15.18.0 起每個事件都因 PowerShell 解析錯誤失敗；改用 & 呼叫運算子
- Windows 使用者需執行一次 npx claude-mem gemini install；update 與自動更新不會重寫 hook
- My Work 以模型判讀 open work-state，信心 ≥0.8 才取代過時狀態；標籤存於 work-view/work-state-labels.json，原始 log 不寫入

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.18.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fixes 
 
 
 Gemini CLI on Windows records again ( #6079 , thanks @tanishqbaweja ). On Windows, Gemini CLI runs hook commands through PowerShell. The hook commands claude-mem wrote started with a quoted path, which PowerShell rejects as a parser error. Every claude-mem Gemini hook (SessionStart, BeforeAgent, AfterTool, AfterAgent, SessionEnd) failed on every event since 15.18.0, so Gemini sessions on Windows saved nothing and got no saved context. Hook commands on Windows now start with PowerShell's & call operator, as the Cursor and Windsurf hooks already do. macOS and Linux are unchanged. 
 Windows Gemini CLI users: run npx claude-mem gemini install once after updating. npx claude-mem update and auto-update do not rewrite Gemini's hooks, so the broken commands stay until you reinstall them. The reinstall replaces the old commands, and npx claude-mem gemini uninstall removes both forms. 
 
 
 Improvements 
 
 My Work shows the real state of open work ( #6038 ). Jev now reads each open work-state item once per version on the 10-minute My Work check and labels it: the state its notes describe, plus which of its fields holds the next step and the result. At confidence 0.8 or higher, My Work shows a judged status in place of a quiet agent's stale doing or missing status (finished becomes Done, not checked; waiting on you becomes Needs you; abandoned becomes Closed). A status the agent set on purpose, such as blocked , is kept. Labels are stored in work-view/work-state-labels.json ; the work-state log itself is never written. Notes are redacted before Jev reads them, calls are paced one a second, and a service refusal or outage stops the run without being retried until the next check. 
 
 CI 
 
 The integration lane launches Chrome once before its tests, so the first browser test no longer fails on the runner's slow first Chrome start ( #6070 , thanks @bulanovk , fixes #6069 ).

</details>