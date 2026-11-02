---
id: inbox_051ed3eb
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-claude-mem-releases-v15-9-0-5738]]"
title: "v15.9.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.9.0
source: claude-mem-releases
published_at: 2026-11-02T18:12:49+00:00
fetched_at: 2026-11-02T23:34:40.791454+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v15.9.0 新增 Devin 支援與遠端 worker 設定，並加強隱私遮蔽與本機路由防護。 **What** 新增 Devin CLI 與 Devin Desktop 的 npx claude-mem install 支援，並新增 CLAUDE_MEM_WORKER_URL 設定，非本機 worker 必須使用 https。此版也在儲存前遮蔽更多憑證類型，並阻擋其他網站透過 localhost 寫入 worker 的部分路由。"
key_points:
  - "新增 Devin 支援：npx claude-mem install 可設定 Devin CLI 與 Devin Desktop 的 hooks，並註冊記憶搜尋工具"
  - "隱私：關閉錯誤回報後，磁碟上已儲存的錯誤也不再送出；儲存前遮蔽 Slack/Discord webhook、Stripe webhook secret、PyPI、SendGrid 等憑證；Kimi 設定備份僅限本人讀取"
  - "新增 CLAUDE_MEM_WORKER_URL：設定值錯誤會直接報錯而非退回預設；非本機 worker 必須使用 https"
tags: [claude-mem, memory, privacy, devin, claude-code]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.9.0

claude-mem v15.9.0 新增 Devin 支援與遠端 worker 設定，並加強隱私遮蔽與本機路由防護。

**What** 新增 Devin CLI 與 Devin Desktop 的 npx claude-mem install 支援，並新增 CLAUDE_MEM_WORKER_URL 設定，非本機 worker 必須使用 https。此版也在儲存前遮蔽更多憑證類型，並阻擋其他網站透過 localhost 寫入 worker 的部分路由。

### 重點
- 新增 Devin 支援：npx claude-mem install 可設定 Devin CLI 與 Devin Desktop 的 hooks，並註冊記憶搜尋工具
- 隱私：關閉錯誤回報後，磁碟上已儲存的錯誤也不再送出；儲存前遮蔽 Slack/Discord webhook、Stripe webhook secret、PyPI、SendGrid 等憑證；Kimi 設定備份僅限本人讀取
- 新增 CLAUDE_MEM_WORKER_URL：設定值錯誤會直接報錯而非退回預設；非本機 worker 必須使用 https

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.9.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 Devin support. npx claude-mem install can now set up Devin CLI and Devin Desktop: hooks are written for you, Devin's tool names are understood, and the memory search tools are registered. ( #5172 , #5276 by @patrickballard and @ssthormess ) 
 My Work refresh on your terms. My Work and Past Focus have a "Refresh now" button ( #5249 by @Kirat0201 ). New settings choose the refresh model per provider: CLAUDE_MEM_WORK_VIEW_CLAUDE_MODEL , CLAUDE_MEM_WORK_VIEW_CODEX_MODEL and CLAUDE_MEM_WORK_VIEW_GEMINI_MODEL ( #5236 by @LucianVane ). 
 Remote workers. New CLAUDE_MEM_WORKER_URL setting. A bad value fails with a clear error instead of falling back, and any worker that isn't on your own machine must use https. ( #5285 by @Kirat0201 ) 
 Privacy and security 
 
 Turning off error reporting now also stops errors already saved on disk from being sent. ( #5272 by @thedotmack ) 
 More secrets are redacted before they are stored: Slack and Discord webhook URLs, Stripe webhook secrets, PyPI, SendGrid, DigitalOcean, Shopify, Docker Hub and GitLab tokens, Basic credentials after Authorization headers, and CLI flags like --auth-token and --client-secret . ( #5277 , #5207 , #5204 , #5224 , #5222 , #5197 by @kevin9327 ; #5205 by @parveen0029 ) 
 Other websites running on localhost can no longer send writes to the worker through the work-state, dedup, corpus and advisor routes. ( #5200 by @DeryFerd ) 
 The Kimi config backup is now readable only by you. ( #5290 by @patrickballard ) 
 
 Fixes you may notice 
 Memory and search 
 
 Switching observer providers mid-conversation no longer duplicates observations. ( #5227 by @liuyinchu ) 
 Repeated turn summaries no longer pile up. ( #5228 by @Dev-0710 ) 
 The transcript watcher no longer loses an end-of-session summary it could not queue. ( #5246 by @liuyinchu ) 
 File searches match whichever way the path separators are written, src/a.ts or src\a.ts . ( #5214 by @rudycelekli ) 
 All-digit dateStart and dateEnd search values are read as epoch milliseconds. ( #5234 by @vinirib ) 
 Restarting the worker during a Chroma rebuild no longer embeds finished documents again. ( #5238 by @vinirib ) 
 Corpora built for merged projects keep the adopted memories, and a failed rebuild no longer loses the saved corpus. ( #5235 by @liuyinchu ; #5291 by @rudycelekli ) 
 Observations with a stray closing tag on the type are still read, and batches survive verification holds. ( #5221 by @Montinou ; #5252 by @Kirat0201 ) 
 Context refresh keeps marker examples you wrote yourself, and CLAUDE.md generation checks duplicate path segments only from the project folder down. ( #5203 by @rudycelekli ; #5232 by @vinirib ) 
 
 My Work and viewer 
 
 Reviews a few characters over a limit no longer fail the whole refresh, and oversized reviews recover after one retry. ( #5230 by @juelpb ; #5286 by @Kirat0201 ) 
 My Work no longer slows other worker requests on large databases, and saving rules or focus rebuilds the view once instead of twice. ( #5284 by @Kirat0201 ; #5239 by @LucianVane ) 
 Viewer filters keep case-variant sessions in project filters and selected categories at zero count. ( #5213 , #5215 by @rudycelekli ) 
 
 Importing history and token usage 
 
 Claude transcripts with whitespace in their JSON are no longer skipped. ( #5289 by @rudycelekli ) 
 Codex and Gemini prompts are no longer imported twice, and legacy Gemini usage is no longer counted twice across migrated copies. ( #5292 , #5217 , #5295 by @rudycelekli ) 
 Token usage stays partial instead of failing when one transcript source can't be read. ( #5294 by @rudycelekli ) 
 
 Providers and accounts 
 
 Worker recycles are no longer reported as authentication failures. ( #5278 by @2023Anita ) 
 macOS: the worker retries the login keychain directly and gives better diagnostics when a credential lookup fails. This may not fix every case in #5250 . ( #5258 by @Kirat0201 ) 
 OpenRouter: endpoints that require reasoning no longer lose the batch; the request is resent once without the setting. ( #5267 by @markjoin123 ) 
 A rejected overage bucket on a request that was served is no longer treated as a refusal. ( #5223 by @beckman55 ) 
 
 Install and CLI 
 
 npx claude-mem adopt --help and npx claude-mem cleanup --help now print help. Before, they ran the command. Not fixed yet: the claude-mem launcher on your PATH still runs them, so use npx to read their help. ( #5288 by @WhitePepperLambSoup ) 
 macOS 27: a launcher the OS killed is rebuilt instead of being kept as foreign. ( #5253 by @REI-330 ) 
 Windows: launcher installs retry short file locks, and npm's claude.exe is used instead of the sh shim. ( #5256 by @HoneyTyagii ; #5198 by @balabommablock-cpu ) 
 Codex: CODEX_HOME is respected, and quoted TOML settings are updated correctly. ( #5216 , #5212 by @rudycelekli ) 
 T3 Code: default Claude and Codex providers are found even when T3 never saved them. ( #5283 by @balabommablock-cpu ) 
 OpenCode: expected registry-only setup calls no longer warn. ( #5264 by @Bl0ck154 ) 
 Hermes: the cached project key for a checkout now expires, so it can't go stale. ( #5287 by @DeryFerd ) 
 claude-md:regenerate reads the database from CLAUDE_MEM_DATA_DIR . ( #5210 by @Bortlesboat ) 
 
 For developers and hosted users 
 
 Server-mode hooks send contentSessionId on semantic injection. ( #5281 by @rich-murphey ) 
 Claude observer per-turn token usage is now logged. ( #5293 by @Kirat0201 ) 
 Claude Duet cloud sessions that can't reach cmem.ai are pointed at the Claude-Mem connector. ( #5243 by @thedotmack ) 
 CI and test improvements. ( #5201 , #5202 by @DeryFerd ; #5254 , #5257 by @xunguangzlj-cloud ) 
 Chinese README terminology updates. ( #5208 by @SaigyoujYuyuko ) 
 
 Thank you 
 This release is mostly community work. Thanks to @rudycelekli , @Kirat0201 , @kevin9327 , @vinirib , @DeryFerd , @patrickballard , @liuyinchu , @LucianVane , @balabommablock-cpu , @xunguangzlj-cloud , @ssthormess , @rich-murphey , @2023Anita , @WhitePepperLambSoup , @markjoin123 , @Bl0ck154 , @HoneyTyagii , @REI-330 , @Dev-0710 , @parveen0029 , @beckman55 , @juelpb , @Montinou , @Bortlesboat and @SaigyoujYuyuko . 
 Full Changelog : v15.8.3...v15.9.0

</details>