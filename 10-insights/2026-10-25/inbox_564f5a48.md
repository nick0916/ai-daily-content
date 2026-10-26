---
id: inbox_564f5a48
date: 2026-10-25
source_ref: "[[00-inbox/2026-10-25/0250-claude-mem-releases-v15-1-0-2000]]"
title: "v15.1.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.1.0
source: claude-mem-releases
published_at: 2026-10-25T07:44:32+00:00
fetched_at: 2026-10-26T02:59:45.983795+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 15.1.0：把監看頁面改用即時資料的 React 版本，並補上語意注入與多項修正。 **How** 舊的 localhost:37777 檢視介面改由 React 版 My Work 取代，直接讀取 worker 的即時資料，更新自動出現，不再需要「Show updates」按鈕。 **What** 新版以每個人類請求一張卡片呈現進度、目標對齊與出貨速度；伺服器端新增逐則提示的語意注入（#5004），Docker 映像內建設定的 embedding 模型（#5003）；MCP 新增選用的 loopback HTTP 傳輸與各 session 獨立 workspace（#5028）。另有 observer、redaction、smart-read 等多項修正，測試也拆成快速與整合兩組。"
key_points:
  - "My Work 檢視介面以 React 重寫並採即時資料，標頭連結至 /viewer 的 Classic 檢視，並顯示 GitHub stars 按鈕"
  - "伺服器新增逐則提示的語意注入（#5004），Docker 映像內建設定的 embedding 模型（#5003）"
  - "MCP 新增選用的 loopback HTTP transport，支援各 session 獨立 workspace（#5028）"
tags: [claude-mem, memory-tool, mcp, release-notes, react-viewer]
topics: [agents.coding_agents, agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.1.0

claude-mem 15.1.0：把監看頁面改用即時資料的 React 版本，並補上語意注入與多項修正。 **How** 舊的 localhost:37777 檢視介面改由 React 版 My Work 取代，直接讀取 worker 的即時資料，更新自動出現，不再需要「Show updates」按鈕。 **What** 新版以每個人類請求一張卡片呈現進度、目標對齊與出貨速度；伺服器端新增逐則提示的語意注入（#5004），Docker 映像內建設定的 embedding 模型（#5003）；MCP 新增選用的 loopback HTTP 傳輸與各 session 獨立 workspace（#5028）。另有 observer、redaction、smart-read 等多項修正，測試也拆成快速與整合兩組。

### 重點
- My Work 檢視介面以 React 重寫並採即時資料，標頭連結至 /viewer 的 Classic 檢視，並顯示 GitHub stars 按鈕
- 伺服器新增逐則提示的語意注入（#5004），Docker 映像內建設定的 embedding 模型（#5003）
- MCP 新增選用的 loopback HTTP transport，支援各 session 獨立 workspace（#5028）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.1.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

claude-mem 15.1.0 
 Highlights 
 
 New My Work viewer (React, live data). The localhost viewer at http://localhost:37777 is replaced by the React My Work viewer on live worker data: one card per human request, progress meters, owner goals, goal alignment, shipping velocity and the build story ( #5010 ). 
 My Work is always live. Updates appear as they arrive; the "Show updates" button is gone. The header now reads "claude-mem", links to the Classic viewer at /viewer , and shows a GitHub stars button. An open request drawer no longer reopens by itself when its request returns to the feed ( #5056 ). 
 Request grouping and progress review. The build story stays under its cap and the story update is told how much room it has ( #5053 , #5054 ); every agent's refresh failure is shown; finished subagents show as finished, and a subagent can be marked finished from its agent card; Claude Code subagent stops are recorded. 
 
 Server 
 
 Per-prompt semantic injection in server mode ( #5004 ). 
 The configured embedding model is baked into the Docker image ( #5003 ). 
 
 MCP 
 
 Opt-in loopback HTTP transport with per-session workspaces ( #5028 ). 
 
 Fixes 
 
 Observer: reasoning gets its own budget and cut-off replies are reported ( #5033 ). 
 Search: unfiltered timelines are scoped to their anchor project ( #5013 ). 
 Worker: cross-origin loopback writes to /api/import are rejected ( #5025 ); Edit payloads carrying new scalar flags keep being trimmed ( #5027 ). 
 Redaction: AWS secret keys under lowercase key names, PGP private key blocks and encrypted PKCS#8 keys ( #5014 , #5017 ). 
 Security: private prompt text stays out of Goals. 
 Smart-read: tree-sitter probe output read when Bun returns a Buffer ( #5024 ), Go type aliases ( #5020 ), Swift extension methods ( #5016 ), symbols ending at column 0 ( #5015 ). 
 Hooks: last_assistant_message mapped in the raw adapter ( #5011 ). 
 Agent runner: npm-installed codex and gemini are found and started. 
 
 Tests 
 
 Suite split into fast and integration lanes; slow, failing and source-grep tests cut ( #5032 ).

</details>