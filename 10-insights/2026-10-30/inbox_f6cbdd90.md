---
id: inbox_f6cbdd90
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/2252-claude-mem-releases-v15-7-0-3b8a]]"
title: "v15.7.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.7.0
source: claude-mem-releases
published_at: 2026-10-30T18:18:54+00:00
fetched_at: 2026-10-30T22:59:48.513853+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 claude-mem 在 Claude 拒答時，自動刷新改由其他帳號執行的問題。 **Why** 在有安裝 Codex 的機器上，約 230 次隱藏的 codex exec 執行動用了擁有者的 ChatGPT 帳號，即使設定 CLAUDE_MEM_PROVIDER=claude。 **How** 被拒絕的回答現在會結束該次刷新，只有無法執行的 agent（未登入、當機）才交給下一個。 **What** v15.7.0 同時新增 My Work 反饋按鈕、note-taker 改用 Claude Code 的 haiku 別名，並補上多項安全修補，包括 Postgres API key 改存 salted scrypt 雜湊。"
key_points:
  - "被拒絕的回答不再轉給下一個已登入 agent，相關問題見 #5189（約 230 次隱藏執行）"
  - "note-taker 預設改用 haiku 別名，自動跟隨最新 Haiku，不再固定 Haiku 4.5 ID"
  - "安全性：Postgres API key 以 salted scrypt 雜湊儲存；redaction 新增 GitLab、Hugging Face、npm token 與 URL 內密碼"
tags: [claude-mem, agent-fallback, codex, security, release-notes]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.7.0

修正 claude-mem 在 Claude 拒答時，自動刷新改由其他帳號執行的問題。

**Why** 在有安裝 Codex 的機器上，約 230 次隱藏的 codex exec 執行動用了擁有者的 ChatGPT 帳號，即使設定 CLAUDE_MEM_PROVIDER=claude。

**How** 被拒絕的回答現在會結束該次刷新，只有無法執行的 agent（未登入、當機）才交給下一個。

**What** v15.7.0 同時新增 My Work 反饋按鈕、note-taker 改用 Claude Code 的 haiku 別名，並補上多項安全修補，包括 Postgres API key 改存 salted scrypt 雜湊。

### 重點
- 被拒絕的回答不再轉給下一個已登入 agent，相關問題見 #5189（約 230 次隱藏執行）
- note-taker 預設改用 haiku 別名，自動跟隨最新 Haiku，不再固定 Haiku 4.5 ID
- 安全性：Postgres API key 以 salted scrypt 雜湊儲存；redaction 新增 GitLab、Hugging Face、npm token 與 URL 內密碼

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.7.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

My Work: refresh stays on your agent, and a Feedback button ( #5190 ) 
 When My Work's automatic refresh got an answer from Claude Code that claude-mem refused (most often a review over 1,200 characters), the whole refresh moved on to the next logged-in agent. On machines with Codex installed, that meant hidden codex exec --ephemeral runs on the owner's ChatGPT account, even with CLAUDE_MEM_PROVIDER=claude ( #5189 : about 230 runs in four days). 
 
 A refused answer now ends that refresh on the agent that gave it. The next scheduled run tries the same agent again, with the existing failure backoff. An agent that can't run at all (not signed in, crashed) still hands the run to the next one. 
 Feedback button in the My Work header, next to Star. It opens a short "My Work feedback" issue form. 
 
 Note-taker always uses the newest Haiku ( #5195 ) 
 The note-taker's default model is now Claude Code's haiku alias, which always resolves to the newest Haiku, instead of a pinned Haiku 4.5 ID. Saved settings that still carry the shipped pinned ID move to the alias on upgrade. A model you typed yourself is left alone. The repo's CLAUDE.md now states this as policy: never pin a dated model ID as a default. 
 My Work and the worker 
 
 Activity-driven background rebuilds of My Work are coalesced, so an open My Work page no longer rebuilds on every database commit ( #5133 , mitigates #5124 ). 
 Work View waits for the database to finish starting before it builds ( #5157 ). 
 The viewer's processing status reconciles after a stream gap ( #5139 ). 
 Daily worker logs older than CLAUDE_MEM_LOG_RETENTION_DAYS (default 30, 0 keeps forever) are pruned. Today's and yesterday's files are always kept ( #5186 ). 
 
 Projects 
 
 Named environments inside a parent Git repository can declare explicit inheritance, so unrelated parent memory no longer leaks into their context ( #5022 ). 
 Oh My Pi keeps transient project memory in model context ( #5183 ). 
 Claude Duet: capture and recall ( #5188 ). 
 
 Media (off by default) 
 
 First phase of image-aware observations: bounded media contracts and a lazy Sharp 0.35.5 converter with size, pixel and deadline limits. CLAUDE_MEM_MEDIA_CAPTURE_ENABLED and CLAUDE_MEM_MEDIA_INFERENCE_ENABLED both default to false ( #4341 ). 
 
 Security 
 
 Executable discovery never looks in the current directory ( #5148 ). 
 Installer URLs are https, and Bun runs from an owner-controlled directory ( #5149 ). 
 The worker rejects cross-origin browser writes to session endpoints and to POST /api/memory/ingest ( #5162 , #5161 ). 
 Postgres API keys are stored as salted scrypt hashes ( #5160 ), and every Postgres sslmode is honored ( #5152 ). 
 Atomic writes use exclusive-create random temp names ( #5151 ). 
 Private tags are stripped before caps, and Hermes' last turn is gated ( #5150 ). 
 Redaction now covers GitLab, Hugging Face and npm tokens ( #5174 ), passwords in URL credentials ( #5173 ), and inbound sync text when local redaction is on ( #5171 ). 
 
 Fixes 
 
 Hook stdin is framed when complete, without waiting for EOF ( #5126 ). 
 A closed session's EPIPE is no longer logged as fatal ( #5177 ). 
 Windows Codex sandbox refusals are explained ( #5140 ). 
 The OpenAI-compatible provider reads the HTTP status from a 200 error envelope with a textual code ( #5191 ). 
 SessionStart counts the memory-use block in its budget without TeamBrain ( #5181 ). 
 A leading ~ in CLAUDE_MEM_DATA_DIR is expanded ( #5179 ). 
 Log tails read only complete lines ( #5166 ). 
 The filtered Chroma fallback narrows to SQLite row ids ( #5154 ). 
 
 Full changelog: v15.6.0...v15.7.0

</details>