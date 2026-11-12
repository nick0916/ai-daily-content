---
id: inbox_76aa4cd6
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0253-claude-mem-releases-v15-16-1-f8e8]]"
title: "v15.16.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.16.1
source: claude-mem-releases
published_at: 2026-11-11T04:58:34+00:00
fetched_at: 2026-11-12T03:03:11.508225+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 v15.16.0 中手動儲存在舊 session 專案失敗（HTTP 500）的重大 bug。 **Why** 15.16.0 的 save_memory 與 POST /api/memory/save 在較早建立 manual session 的專案中，因 sdk_sessions.memory_session_id 的 UNIQUE 限制而失敗，該專案所有儲存都會失敗。 **How** 改為找到並重用舊的 session，而不是建立重複 ID；已刪除的 session 仍會取得新 ID。 **What** 同時新增兩個預設關閉的功能：CLAUDE_MEM_SKILLS_DISABLED 可停用內建 skill，CLAUDE_MEM_LINE_ANCHORS_ENABLED 讓檔案 context 的 observation 指向程式碼目前所在的行號；另修正 OpenClaw 2026.11.2 安裝器與 Warp 解除安裝殘留的問題。"
key_points:
  - "15.16.0 使用者應升級至 15.16.1，否則舊 session 專案的手動儲存會回 HTTP 500"
  - "CLAUDE_MEM_SKILLS_DISABLED 可用逗號字串或 JSON 陣列停用內建 skill（#5837）"
  - "CLAUDE_MEM_LINE_ANCHORS_ENABLED 設為 true 後，過往 observation 會標示目前行號（如 @L123），搬移時標示 code changed since（#5841）"
tags: [claude-mem, bugfix, skills, openclaw, hotfix]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.16.1

修正 v15.16.0 中手動儲存在舊 session 專案失敗（HTTP 500）的重大 bug。

**Why** 15.16.0 的 save_memory 與 POST /api/memory/save 在較早建立 manual session 的專案中，因 sdk_sessions.memory_session_id 的 UNIQUE 限制而失敗，該專案所有儲存都會失敗。

**How** 改為找到並重用舊的 session，而不是建立重複 ID；已刪除的 session 仍會取得新 ID。

**What** 同時新增兩個預設關閉的功能：CLAUDE_MEM_SKILLS_DISABLED 可停用內建 skill，CLAUDE_MEM_LINE_ANCHORS_ENABLED 讓檔案 context 的 observation 指向程式碼目前所在的行號；另修正 OpenClaw 2026.11.2 安裝器與 Warp 解除安裝殘留的問題。

### 重點
- 15.16.0 使用者應升級至 15.16.1，否則舊 session 專案的手動儲存會回 HTTP 500
- CLAUDE_MEM_SKILLS_DISABLED 可用逗號字串或 JSON 陣列停用內建 skill（#5837）
- CLAUDE_MEM_LINE_ANCHORS_ENABLED 設為 true 後，過往 observation 會標示目前行號（如 @L123），搬移時標示 code changed since（#5841）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.16.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fix 
 
 Manual saves work again in projects with older manual sessions. In v15.16.0, save_memory (and POST /api/memory/save ) returned HTTP 500 with UNIQUE constraint failed: sdk_sessions.memory_session_id in any project whose manual session was created before 15.16.0 with an older session ID shape. Every save in that project failed. claude-mem now finds and reuses that older session instead of trying to create a duplicate. Deleted sessions still get a fresh ID, as in 15.16.0 ( #5842 ). 
 
 If you are on 15.16.0, update to 15.16.1. 
 New (both off by default) 
 
 Opt out of bundled skills: list skill names in CLAUDE_MEM_SKILLS_DISABLED in ~/.claude-mem/settings.json , as a comma-separated string or a JSON array (for example "make-plan,do,smart-explore" ). The list is re-applied after installs, repairs and marketplace updates; new skills stay enabled unless you name them ( #5837 , thanks @liuyinchu , closes #5132 ). 
 Line anchors in file context: set CLAUDE_MEM_LINE_ANCHORS_ENABLED to "true" and past observations about a file point at the line where that code is now ( @L123 ), or say (code changed since) when it moved away. Nothing is guessed. With the setting off, nothing is recorded and the hook output is unchanged ( #5841 , thanks @devkancheti4-design , closes #4943 ). 
 
 Fixes 
 
 OpenClaw: the installer works on OpenClaw 2026.11.2 again, and current OpenClaw records prompts, injects context and summarizes sessions without the removed before_agent_start hook. Older OpenClaw versions behave as before ( #5840 , fixes #5838 , reported by @JesseFranzen ). 
 Warp uninstall: npx claude-mem uninstall now removes the claude-mem MCP server that install --ide warp adds to ~/.warp/.mcp.json , instead of leaving it pointed at the deleted plugin ( #5839 , thanks @tanishqbaweja ). 
 Telemetry IDs: recording a consent decision (installer prompt, telemetry enable , telemetry disable ) keeps the saved anonymous ID, so one install no longer shows up as two. The telemetry enable disclosure now lists the events actually sent ( #5836 , thanks @wiesenthal ). 
 
 Full changelog: v15.16.0...v15.16.1

</details>