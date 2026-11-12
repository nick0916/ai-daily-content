---
id: inbox_915bba79
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0253-claude-mem-releases-v15-16-0-e6c9]]"
title: "v15.16.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.16.0
source: claude-mem-releases
published_at: 2026-11-11T00:34:23+00:00
fetched_at: 2026-11-12T03:03:11.508563+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 My Work 刷新可改用 API provider 執行，無登入 Claude Code 的環境也能使用。 **Why** 原本 My Work 需要已登入的 Claude Code、Codex 或 Gemini CLI，OpenCode、DSH 等環境無法使用。 **How** 設定 CLAUDE_MEM_WORK_VIEW_AGENT=api，改用已選取的 openrouter、openai-compatible 等 provider；若此設定為空，刷新不會退回已登入的 Claude Code，未選擇時不執行也不花費。 **What** 同版另加入 GitHub 官方 MCP create_pull_request 建立的 PR 作為 My Work 產物、UberLLM 預設 preset、可調整的 CLAUDE_MEM_HOOK_HANDOFF_TIMEOUT_MS（預設 250），並清理 Claude Code marketplace 更新遺留的舊版本資料夾（一例 21 版、約 16 GB），另有約 130 項小修正。"
key_points:
  - "CLAUDE_MEM_WORK_VIEW_AGENT=api 讓 My Work 使用已選的 API provider；未明確選擇時不會 fallback 到付費 agent"
  - "GitHub 官方 MCP create_pull_request 建立的 PR 會顯示為 My Work 產物，且僅接受 URL 符合指定 repo 的結果（#5809）"
  - "舊 plugin 版本清理：保留執行中與已登記版本，開機後與每小時掃描一次（#5685）"
tags: [claude-mem, my-work, openrouter, github-mcp, plugin-cache]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.16.0

讓 My Work 刷新可改用 API provider 執行，無登入 Claude Code 的環境也能使用。

**Why** 原本 My Work 需要已登入的 Claude Code、Codex 或 Gemini CLI，OpenCode、DSH 等環境無法使用。

**How** 設定 CLAUDE_MEM_WORK_VIEW_AGENT=api，改用已選取的 openrouter、openai-compatible 等 provider；若此設定為空，刷新不會退回已登入的 Claude Code，未選擇時不執行也不花費。

**What** 同版另加入 GitHub 官方 MCP create_pull_request 建立的 PR 作為 My Work 產物、UberLLM 預設 preset、可調整的 CLAUDE_MEM_HOOK_HANDOFF_TIMEOUT_MS（預設 250），並清理 Claude Code marketplace 更新遺留的舊版本資料夾（一例 21 版、約 16 GB），另有約 130 項小修正。

### 重點
- CLAUDE_MEM_WORK_VIEW_AGENT=api 讓 My Work 使用已選的 API provider；未明確選擇時不會 fallback 到付費 agent
- GitHub 官方 MCP create_pull_request 建立的 PR 會顯示為 My Work 產物，且僅接受 URL 符合指定 repo 的結果（#5809）
- 舊 plugin 版本清理：保留執行中與已登記版本，開機後與每小時掃描一次（#5685）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.16.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New 
 
 My Work refresh on your API provider (opt-in): set CLAUDE_MEM_WORK_VIEW_AGENT=api to run the My Work refresh on the provider you already selected ( openrouter , openai-compatible , or the legacy cmem spelling). Installs with no logged-in Claude Code, Codex or Gemini CLI (for example OpenCode or DSH hosts) can now use My Work. With an API provider selected and the setting empty, the refresh no longer falls back to a logged-in Claude Code: no agent runs and nothing is spent until you choose one ( #5674 , thanks @bulanovk ). 
 GitHub MCP pull requests in My Work: pull requests created through GitHub's official MCP create_pull_request tool now show up as My Work products. Only completed results whose URL matches the requested repository are accepted ( #5809 , thanks @Afloat16 ). 
 UberLLM preset: uberllm is now a preset of the openai-compatible provider ( https://api.uberllm.dev/v1 , default model deepseek/deepseek-v4.1-flash ) ( #5706 , thanks @PSA-Team-source ). 
 Tunable live handoff timeout: CLAUDE_MEM_HOOK_HANDOFF_TIMEOUT_MS (default 250) sets the budget for the single live handoff from a hook to the worker, and a missed handoff is now logged at WARN instead of DEBUG ( #5831 , thanks @mohitdixit02 ). 
 
 Notable fixes 
 
 Plugin cache cleanup: the worker now prunes old version folders that Claude Code's marketplace updates leave in ~/.claude/plugins/cache/thedotmack/claude-mem/ (one report: 21 versions, about 16 GB). It keeps the running copy and the registered version, and sweeps after boot settles and then hourly ( #5685 , thanks @MaxWang007 ). 
 Windows antivirus noise: install, update and launcher rebuilds no longer start a hidden PowerShell when the launcher folder is already on PATH, the pattern Kaspersky flagged ( #5835 , reported by @Ali-Sabri-0 ). 
 My Work language: when CLAUDE_MEM_WORK_VIEW_TEXT_LANGUAGE is empty, every refresh step now writes in the system locale's language, so one run no longer mixes languages ( #5669 , thanks @0xABCD01 ). 
 My Work idle cost: idle polling no longer rescans every synced row, and the live overview, focus-area merging and heavy panels do less work per update ( #5834 ). 
 Backups: a declined backup run returns a failure, saved backups are reported separately from retention errors, backup intervals beyond the timer limit are honored, and restore rejects stamped snapshots missing worker tables ( #5750 , #5781 , #5784 , #5684 , thanks @Kirat0201 ). 
 Shell setup: the launcher PATH block and the legacy uninstall alias are written atomically, Cowork stages spooled events under $HOME when the host sets it, and Hermes keeps permanent HTTP client errors out of its circuit breaker ( #5680 , #5679 , #5677 , #5678 , thanks @DeryFerd ). 
 OpenCode: the bash tool is reported as Bash , so SKIP_BASH_PATTERNS applies ( #5668 , thanks @ryrenz ). 
 Sync: a failed Chroma cleanup after a delete is retried ( #5673 , thanks @Zhong-fan ). 
 SessionStart: the cache read and compose steps share one body budget, so a cached body is served only when it fits ( #5686 , thanks @Varshith-Kali ). 
 
 More fixes 
 About 130 smaller fixes from @Afloat16 across capture, sync, search, context, import, transcripts, media, the server, and the Codex, OpenCode, OpenClaw, Hermes, Grok, Kimi, Gemini, Pi, Goose, Notion and Telegram integrations. Highlights: 
 
 Search and context: literal project keys and file paths are preserved through recall, merges and caching; Unicode and combining marks survive query words and snippet limits; cached context expires after restores and row replacements; the largest fitting timeline prefix is kept. 
 Sync and memory: session titles commit with their outbox mutation and get receiver redaction; manual saves and new prompts work after a session deletion; note revisions survive title dedup. 
 Transcripts and import: multipart Codex messages, paired patch results and zstd frame seams are read correctly; reasoning stays out of final answers; OpenCode, Gemini and restored summaries import without duplicates or lost prompts. 
 Server and providers: API key derivation stays off the request loop; cancellations propagate through retries and compression; split token usage is metered on compatible replies; memory content is sanitized before storage. 
 Media: image ordinals, Read evidence across path spellings, and advertised image dimension bounds are preserved; inline allowance is charged only for accepted images. 
 
 Also from @Kirat0201 : file history follows whole project merges, interactive timeline search honors project lists, and unified search keeps literal filePath values ( #5789 , #5787 , #5785 ). 
 Full changelog: v15.15.2...v15.16.0

</details>