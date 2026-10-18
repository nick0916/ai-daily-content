---
id: inbox_01b30c8d
date: 2026-10-11
source_ref: "[[00-inbox/2026-10-11/0256-ruflo-releases-v3-56-6-windows-hook-launch-fix-sessions-d01b]]"
title: "v3.56.6 — Windows hook launch fix, SessionStart risk scanner, cli-core/shared fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.56.6
source: ruflo-releases
published_at: 2026-10-11T16:49:28+00:00
fetched_at: 2026-10-18T03:20:23.510701+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 發布 v3.56.6 patch（@claude-flow/cli、claude-flow、ruflo），CLI 現 pin 住當日稍早發布的 @claude-flow/cli-core 3.7.1 與 @claude-flow/shared 3.0.3。最重要的修正是 Windows hook 啟動方式：改用 `node -e` 取代 `cmd /c`，因為後者會啟動互動式 cmd，把 hook 的 JSON payload 當成指令執行並產生多餘檔案（#4045）；signed helpers 因此變更並重新簽署（#4053）。另外 settings.json 風險掃描器現在會在自動的 SessionStart hook 執行，且 encoded-PowerShell 比對改為線性時間（#4052、#4053）。Trajectory-end 回饋即使已記錄 steps 也會被索引（#3662、#4051）。cli-core 3.7.1 / shared 3.0.3 修正 JSON memory backend、表格與進度輸出、RVF event log 與 circuit breaker（#4061）。Plugin 方面（不影響 npm）：ruflo-cost-tracker 保留 Codex usage 歸屬（#4048）、ruflo-swarm 為原生 Codex hook discovery 提供 host 專屬 no-op manifest（#4050），ruflo-adr 升至 0.5.5。對 Windows 使用者與依賴 hook 安全掃描的團隊影響最大。"
key_points:
  - "Windows hook 以 `node -e` 取代 `cmd /c`，避免互動式 cmd 把 hook JSON payload 當指令執行而產生雜檔（#4045）"
  - "settings.json 風險掃描器改在自動 SessionStart hook 執行，encoded-PowerShell 比對降為線性時間（#4052）"
  - "cli-core 3.7.1 / shared 3.0.3 一批修正：JSON memory backend、RVF event log、circuit breaker（#4061）"
tags: [ruflo, windows-hooks, sessionstart-hook, risk-scanner, patch-release]
topics: [agents.coding_agents, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.56.6 — Windows hook launch fix, SessionStart risk scanner, cli-core/shared fixes

Ruflo 發布 v3.56.6 patch（@claude-flow/cli、claude-flow、ruflo），CLI 現 pin 住當日稍早發布的 @claude-flow/cli-core 3.7.1 與 @claude-flow/shared 3.0.3。最重要的修正是 Windows hook 啟動方式：改用 `node -e` 取代 `cmd /c`，因為後者會啟動互動式 cmd，把 hook 的 JSON payload 當成指令執行並產生多餘檔案（#4045）；signed helpers 因此變更並重新簽署（#4053）。另外 settings.json 風險掃描器現在會在自動的 SessionStart hook 執行，且 encoded-PowerShell 比對改為線性時間（#4052、#4053）。Trajectory-end 回饋即使已記錄 steps 也會被索引（#3662、#4051）。cli-core 3.7.1 / shared 3.0.3 修正 JSON memory backend、表格與進度輸出、RVF event log 與 circuit breaker（#4061）。Plugin 方面（不影響 npm）：ruflo-cost-tracker 保留 Codex usage 歸屬（#4048）、ruflo-swarm 為原生 Codex hook discovery 提供 host 專屬 no-op manifest（#4050），ruflo-adr 升至 0.5.5。對 Windows 使用者與依賴 hook 安全掃描的團隊影響最大。

### 重點
- Windows hook 以 `node -e` 取代 `cmd /c`，避免互動式 cmd 把 hook JSON payload 當指令執行而產生雜檔（#4045）
- settings.json 風險掃描器改在自動 SessionStart hook 執行，encoded-PowerShell 比對降為線性時間（#4052）
- cli-core 3.7.1 / shared 3.0.3 一批修正：JSON memory backend、RVF event log、circuit breaker（#4061）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.56.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.6 (latest, alpha, v3alpha). The CLI now pins @claude-flow/cli-core 3.7.1 and @claude-flow/shared 3.0.3 (published earlier today). 
 Fixed 
 
 Windows hooks launch through node -e instead of cmd /c , which started an interactive cmd that executed the hook JSON payload and created stray files ( #4045 ). Signed helpers changed and were re-signed ( #4053 ). 
 The settings.json risk scanner now runs on the automatic SessionStart hook; encoded-PowerShell matching is linear time ( #4052 , #4053 ). 
 Trajectory-end feedback is indexed even when steps were recorded ( #3662 , #4051 ). 
 cli-core 3.7.1 / shared 3.0.3: JSON memory backend, table and progress output, RVF event log and circuit breaker fixes ( #4061 ). 
 
 Plugins (no npm impact) 
 
 ruflo-cost-tracker : preserve Codex usage ownership ( #4048 ). ruflo-swarm : host-specific no-op manifest for native Codex hook discovery ( #4050 ). ruflo-adr 0.5.5. 
 
 Contributors 
 Thanks to @rudycelekli for the reviewed batch behind #4061 (PRs #4020 - #4026 , #4028 - #4030 , #4032 , #4033 , #4035 , #4037 ) and to @Devesh-Maheshwari for #4048 .

</details>