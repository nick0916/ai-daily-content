---
id: inbox_8e270dfb
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/2337-claude-code-releases-v2-1-312-8d43]]"
title: "v2.1.312"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.312
source: claude-code-releases
published_at: 2026-10-27T20:24:20+00:00
fetched_at: 2026-10-27T23:44:18.727471+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 的例行修正版，補強企業身分、長檔案保護、提示詞設定與雲端工作階段的穩定性。 **Why** 企業環境常用 Microsoft Entra ID 等非標準身分欄位，且大型設定檔與第三方模型部署名稱容易造成誤判或資料被覆寫。 **How** 新增 `oidc.user_id_claim` 讓 gateway 可用 `sub` 以外的 id_token claim 識別使用者；Write 遇到只讀到開頭的大檔會要求 Claude 讀完或就地編輯；對無法辨識的模型名稱改用較短的系統提示詞。 **What** Claude Code v2.1.312 新增 `oidc.user_id_claim`（如 Entra 的 `oid`）與全螢幕點擊「to send now」立即送出佇列訊息。修正大型 CLAUDE.md 被覆寫、managed settings 在 VS Code 登入後未取得、PDF 讀取失敗等問題。Bedrock、Vertex、Foundry、Mantle 遇到自訂部署名稱改用短系統提示詞（可用 `CLAUDE_CODE_SIMPLE_SYSTEM_PROMPT=0` 保留完整版），prompt/agent hooks 每個 session 最多同時跑 24 個，並停止送出 `claude_code.safety_event` OpenTelemetry 事件。"
key_points:
  - "新增 `oidc.user_id_claim`：Claude apps gateway 可用 sub 以外的 id_token claim 識別使用者，例如 Microsoft Entra ID 的 `oid`"
  - "Bedrock／Vertex／Foundry／Mantle 遇到無法辨識的模型名稱（自訂部署名、inference profile ARN）改用較短系統提示詞，可設 `CLAUDE_CODE_SIMPLE_SYSTEM_PROMPT=0` 保留完整版；自動模型切換也涵蓋這類名稱，可用 `CLAUDE_CODE_DISABLE_REFUSAL_FALLBACK=1` 關閉"
  - "prompt/agent hooks 每 session 最多同時 24 個（含 sub-agents），另加最多 12 個等待超過事件 timeout 的；subagent 的 autoCompactWindow 現可調低 `CLAUDE_CODE_AUTO_COMPACT_WINDOW`，但不會調高"
tags: [claude-code, release-notes, oidc, hooks, bedrock-vertex]
topics: [agents.coding_agents]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.312

Claude Code 的例行修正版，補強企業身分、長檔案保護、提示詞設定與雲端工作階段的穩定性。

**Why** 企業環境常用 Microsoft Entra ID 等非標準身分欄位，且大型設定檔與第三方模型部署名稱容易造成誤判或資料被覆寫。

**How** 新增 `oidc.user_id_claim` 讓 gateway 可用 `sub` 以外的 id_token claim 識別使用者；Write 遇到只讀到開頭的大檔會要求 Claude 讀完或就地編輯；對無法辨識的模型名稱改用較短的系統提示詞。

**What** Claude Code v2.1.312 新增 `oidc.user_id_claim`（如 Entra 的 `oid`）與全螢幕點擊「to send now」立即送出佇列訊息。修正大型 CLAUDE.md 被覆寫、managed settings 在 VS Code 登入後未取得、PDF 讀取失敗等問題。Bedrock、Vertex、Foundry、Mantle 遇到自訂部署名稱改用短系統提示詞（可用 `CLAUDE_CODE_SIMPLE_SYSTEM_PROMPT=0` 保留完整版），prompt/agent hooks 每個 session 最多同時跑 24 個，並停止送出 `claude_code.safety_event` OpenTelemetry 事件。

### 重點
- 新增 `oidc.user_id_claim`：Claude apps gateway 可用 sub 以外的 id_token claim 識別使用者，例如 Microsoft Entra ID 的 `oid`
- Bedrock／Vertex／Foundry／Mantle 遇到無法辨識的模型名稱（自訂部署名、inference profile ARN）改用較短系統提示詞，可設 `CLAUDE_CODE_SIMPLE_SYSTEM_PROMPT=0` 保留完整版；自動模型切換也涵蓋這類名稱，可用 `CLAUDE_CODE_DISABLE_REFUSAL_FALLBACK=1` 關閉
- prompt/agent hooks 每 session 最多同時 24 個（含 sub-agents），另加最多 12 個等待超過事件 timeout 的；subagent 的 autoCompactWindow 現可調低 `CLAUDE_CODE_AUTO_COMPACT_WINDOW`，但不會調高

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.312)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added oidc.user_id_claim to the Claude apps gateway, to identify people by an id_token claim other than sub , such as Microsoft Entra ID's oid 
 Added click to send: in fullscreen, clicking the "to send now" hint under a queued message sends it right away, as its key does 
 Fixed managed settings and organization policy not being fetched for the rest of the session after signing in from the VS Code extension 
 Fixed Claude overwriting a very large CLAUDE.md, rules file or @-included file in a subdirectory after seeing only its start; Write now asks Claude to read it all or edit in place 
 Fixed per-directory and paths: skills not being found after a Bash cd deeper into a git repository 
 Fixed a rare case where the first reply after resuming a session in the terminal could be missing the next time the session was resumed 
 Fixed a command with an invalid name stopping all commands from loading, which could leave claude -p with no output 
 Fixed the Read tool sometimes failing on PDF pages with "pdftoppm failed: Could not write image" when the clean-up of old session files ran at the same time 
 Fixed the spinner, OpenTelemetry effort values and transcripts naming a newly picked effort level during a task before the model applied it; they now show the level in force 
 Fixed the /model and /effort cache warning saying the re-read waits for your next message; a change made while Claude is working can trigger it sooner 
 Fixed some sessions showing as waiting on you when the last message only mentioned items waiting on you mid-sentence 
 Fixed agent view restoring input text on the next launch after it was cleared with Ctrl+C just before exiting 
 Fixed agent view reopening in shell mode after exiting with Ctrl+D from an empty ! input 
 Fixed vim mode d , c and y with a gj or gk count larger than the lines left deleting or copying text; like Vim, they now only move the cursor 
 Fixed /verify showing a long description meant for Claude in /help and the / command menu instead of a short one 
 Improved the prompt's effort indicator: a change made mid-task now says it may wait for your next message, and the note clears when it no longer applies 
 Improved WebFetch errors in cloud sessions: a host that does not resolve is now explained as possibly outside the allowed network domains, so Claude names the host to allow 
 Changed Bedrock, Vertex, Foundry and Mantle to use the shorter system prompt for model names Claude Code doesn't recognize, such as custom deployment names and inference profile ARNs, even when they front Sonnet or Haiku; set CLAUDE_CODE_SIMPLE_SYSTEM_PROMPT=0 to keep the full prompt 
 Changed automatic model switches after a flagged message to also cover model names Claude Code doesn't recognize, such as custom deployment names; set CLAUDE_CODE_DISABLE_REFUSAL_FALLBACK=1 to turn them off 
 Changed usage limit messages to call the 5-hour window the "5-hour limit" instead of the "session limit" 
 Changed cloud sessions started from the CLI to get their names and branch names from the server 
 Changed prompt and agent hooks to run at most 24 at a time per session, sub-agents included, plus at most 12 that have waited longer than their event's timeout; a timeout under 1 second now counts as 1 second 
 Changed a subagent's autoCompactWindow to lower the window set by CLAUDE_CODE_AUTO_COMPACT_WINDOW , where it had no effect before; it still never raises that window 
 Changed OpenTelemetry mcp_server.name to report the real name of fixed-URL remote MCP servers declared by plugins from the official Anthropic marketplace, instead of custom 
 Changed Claude Code to stop sending the claude_code.safety_event OpenTelemetry event 
 [VSCode] Fixed sessions ending on a bare exit code when your organization's settings couldn't be loaded or were refused at startup; the tab now says why and offers Retry or Sign in again 
 [VSCode] Changed usage limit resets to show a clock time ("Resets at 3:10 PM") and to say "5-hour limit" 
 [Cloud sessions] Added an effort level to the model picker when you create or edit a routine that runs in the cloud 
 [Cloud sessions] Added a Bash editor with colors, line numbers and a Copy button to the setup script box in cloud environment settings 
 [Cloud sessions] Improved the step shown when Claude adds a repository to a cloud session: opening it now shows a short table of what happened instead of raw JSON 
 [Cloud sessions] Fixed resending an unchanged message after a failed send in a cloud session sometimes running it twice 
 [Cloud sessions] Fixed a failed cloud environment creation showing its error only as a toast outside the open dialog; it now appears inside the dialog 
 [Cloud sessions] Fixed Edit in a routine's menu on the Routines page going to the routine's page without opening its edit dialog 
 [Remote Control] Fixed an unarchived Remote Control session showing as working until a computer reconnected; it now shows as idle 
 [Claude Tag] Improved Claude Tag's retry notice in Slack to name the model in use, or say rate limits were hit, instead of a generic API error 
 [Claude Tag] Fixed a Claude Tag channel's on/off switch and agent settings falling back to workspace defaults when an older private Slack channel goes public and gets a new ID 
 [Claude Tag] Fixed Claude in Slack not replying in channels whose environment has network access set to None 
 [Claude Tag] Fixed Claude in Slack sometimes posting a file in the wrong thread when it was answering in another thread of the same channel 
 [Code Review] Fixed Code Review reviewing an outdated commit, or none at all, when GitHub delivered a push event late; it now reviews the pull request's current commit

</details>