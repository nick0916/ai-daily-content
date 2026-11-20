---
id: inbox_52ef4409
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0105-codex-releases-0-171-0-4b84]]"
title: "0.171.0"
url: https://github.com/openai/codex/releases/tag/rust-v0.171.0
source: codex-releases
published_at: 2026-11-20T00:47:14+00:00
fetched_at: 2026-11-20T01:11:01.493178+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex 0.171.0 把新模型加進選單，並預設開啟終端機工作區介面。 **What** OpenAI Codex（Rust 版 rust-v0.171.0）將 GPT-6.2 Sol 與 Astra 加入 model catalog，並以 Sol 為預設選項。TUI workspace 改為預設啟用，支援可搜尋的文件預覽、圖片預覽與 subagent 對話紀錄。新增 `codex exec --remote` 可在既有 app server 上啟動或接續非互動 session，另有 `/rc`、`/remote` 指令與可設定的復原/重做快捷鍵；修正多項問題，包括切換 session 時草稿與排隊輸入遺失、切換工作目錄時 permission profile 被重置，以及企業 MCP 登入對不發 refresh token 的 IdP 失效。工具鏈升級到 Rust 1.99.1。"
key_points:
  - "GPT-6.2 Sol 與 Astra 加入 model catalog，Sol 為預設選項（#62106）"
  - "TUI workspace 預設啟用，含文件/圖片預覽與 subagent transcript（#61352 等）"
  - "新增 `codex exec --remote`、`/rc`、`/remote`，以及可選的 MCP 狀態列（需啟用 tui_extensions_statusline）"
tags: [openai-codex, release-notes, gpt-6-2, tui, mcp]
topics: [agents.coding_agents, foundation_models.gpt]
importance: 3
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.171.0

OpenAI Codex 0.171.0 把新模型加進選單，並預設開啟終端機工作區介面。

**What** OpenAI Codex（Rust 版 rust-v0.171.0）將 GPT-6.2 Sol 與 Astra 加入 model catalog，並以 Sol 為預設選項。TUI workspace 改為預設啟用，支援可搜尋的文件預覽、圖片預覽與 subagent 對話紀錄。新增 `codex exec --remote` 可在既有 app server 上啟動或接續非互動 session，另有 `/rc`、`/remote` 指令與可設定的復原/重做快捷鍵；修正多項問題，包括切換 session 時草稿與排隊輸入遺失、切換工作目錄時 permission profile 被重置，以及企業 MCP 登入對不發 refresh token 的 IdP 失效。工具鏈升級到 Rust 1.99.1。

### 重點
- GPT-6.2 Sol 與 Astra 加入 model catalog，Sol 為預設選項（#62106）
- TUI workspace 預設啟用，含文件/圖片預覽與 subagent transcript（#61352 等）
- 新增 `codex exec --remote`、`/rc`、`/remote`，以及可選的 MCP 狀態列（需啟用 tui_extensions_statusline）

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.171.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New Features 
 
 Added GPT-6.2 Sol and Astra to model catalogs, with Sol as the default catalog selection. ( #62106 ) 
 Enabled the TUI workspace by default, with searchable document previews, image previews, and subagent transcripts alongside the main conversation. ( #61352 , #61888 , #61889 , #61919 , #62157 ) 
 Added configurable undo and redo shortcuts to the non-Vim prompt composer, including restoration of attachments and large pastes. ( #61954 ) 
 Added codex exec --remote to start or resume noninteractive sessions on an existing app server. ( #61707 ) 
 Added /rc and /remote to manage local remote control and display device pairing codes from the TUI. ( #62121 ) 
 Added custom MCP status line selection and authoring through /statusline when tui_extensions_statusline is enabled. ( #61979 , #61988 , #62037 ) 
 
 Bug Fixes 
 
 Preserved drafts, queued follow-ups, and interrupted input with their original threads when switching or resuming sessions. ( #61216 ) 
 Kept permission profiles intact when changing working directories. ( #61195 ) 
 Prevented late completion events from cancelling approvals for a newer turn. ( #61801 ) 
 Preserved earlier edits in aggregate diffs when steering an active turn. ( #61820 ) 
 Fixed scrolling that inserted stray characters, composer caret jumps, and redraws using stale terminal dimensions. ( #62139 , #62174 , #62175 ) 
 Fixed enterprise MCP sign-in for identity providers that issue ID tokens without refresh tokens. ( #62129 ) 
 
 Chores 
 
 Updated source builds and release tooling to Rust 1.99.1. ( #61205 ) 
 Updated XML dependencies and removed obsolete security advisory exceptions. ( #62068 ) 
 
 Changelog 
 Full Changelog: rust-v0.170.0...rust-v0.171.0 
 
 #61178 Enable conversation-scoped speed selection for Cloud turns @bc-openai 
 #61180 Reclaim abandoned trusted Git repositories @etraut-openai 
 #61181 Fix pagination for unindexed threads sorted by ascending recency @etraut-openai 
 #61182 Support renaming cloud threads @bc-openai 
 #61183 Fix fork parent metadata in reconstructed TUI sessions @fcoury-oai 
 #61185 Defer Guardian context limits to request preparation @ioanbudea-OAI 
 #61186 Keep plan item IDs unique after completion @neerajrj-oai 
 #61187 Add authenticated GCS caching for Bazel CI and releases @dkovalenko-oai 
 #61194 Remove redundant legacy permission helpers @ioanbudea-OAI 
 #61195 Preserve permission profiles across working directory updates @ioanbudea-OAI 
 #61196 Clear inline image previews before history insertion can scroll them @dob-oai 
 #61197 Clarify remote message board and clock documentation @anp-oai 
 #61198 Add graceful agent-tree suspension and recovery @bryanashley 
 #61199 Align rollout trace replay with the same-binary contract @cassirer-openai 
 #61200 Unify TUI status content and layout caching in StatusLine @fcoury-oai 
 #61201 Clean up Rust error handling and OTLP test assertions @ioanbudea-OAI 
 #61205 Upgrade the Rust toolchain to 1.99.1 @ioanbudea-OAI 
 #61206 Enforce Linux seccomp restrictions for x32 syscalls @dhavalkapil-oai 
 #61207 Add SPIFFE JWT-SVID support for workload identity authentication @cooper-oai 
 #61210 Retain TUI delegation prompts in thread model history @won-openai 
 #61211 Add local status line provider configuration @joesavona 
 #61212 Add persistence support for status line provider selections @joesavona 
 #61213 Support model catalog Apps usage instructions @goodman-oai 
 #61215 Track dictation usage from accepted user inputs @chrisdong-oai 
 #61216 Preserve thread input across TUI session resumes @bc-openai 
 #61218 Hide attached threads from the agents overview @fcoury-oai 
 #61219 Hide TUI status details for read-only history @joesavona 
 #61220 Deduplicate overlapping Apps startup tool listings @charliemarsh-oai 
 #61221 Forward repeated signals through the npm wrapper @etraut-openai 
 #61222 Store rollout trace payloads in compressed shards @cassirer-openai 
 #61224 Include AppX event IDs in Windows runtime registration errors @zm-oai 
 #61227 Include Win32 error codes in MXC process launch failures @zm-oai 
 #61228 Add a missing semicolon in the realtime call test helper @bc-openai 
 #61248 Add MCP inventory support for statusline providers @joesavona 
 #61249 Resolve MCP statusline providers and read thread-scoped resources @joesavona 
 #61250 Add bounded streaming discovery for statusline providers @joesavona 
 #61251 Refactor history and notes tools around backend traits @euroelessar 
 #61253 Move rollout trace recording to a background worker @cassirer-openai 
 #61254 Fix Bazel tool resolution for bubblewrap and voice builds @bencodes-oai 
 #61255 Honor PIP_INDEX_URL for V8 Python dependencies @bencodes-oai 
 #61256 Block request_key in Linux network sandbox filters @dhavalkapil-oai 
 #61257 Preserve MCP registration scope across client operations @sayan-oai 
 #61259 Update realtime model and honor provider-specific voice defaults @cooper-oai 
 #61260 Accept ERS v1 and v2 tunnel JWTs @dines-oai 
 #61263 Refactor session window access and async compaction test setup @maxj-oai 
 #61264 Enable gzip and zstd support in the shared HTTP client @joeyp-openai 
 #61272 Set the environment field in statusline MCP requests @anp-oai 
 #61276 Consolidate Windows filesystem helper sandbox preparation @viyatb-oai 
 #61283 Accept explicit contribution context for MCP runtime configuration @sayan-oai 
 #61286 Add and preserve the marketplace auto-update setting @smurching-oai 
 #61337 Centralize managed network proxy startup @viyatb-oai 
 #61338 Record host-confirmed Code Mode wait targets in rollout traces @tz-openai 
 #61339 Add session-scoped stores for stable model-facing IDs @anp-oai 
 #61341 Add opt-in prompt image sanitization @vivi 
 #61342 Cancel abandoned cloud thread list requests @bc-openai 
 #61343 Title saved side chats from their first direct input @fcoury-oai 
 #61344 Add per-item retention policies for injected history @vivi 
 #61345 Add opt-in elastic budgeting for asynchronous Guardian requests @ioanbudea-OAI 
 #61346 Apply elastic entry caps to Guardian classifier evidence @ioanbudea-OAI 
 #61347 Reserve item ID overhead before elastic context allocation @ioanbudea-OAI 
 #61349 Add managed CA defaults for Deno and Google Cloud SDK @viyatb-oai 
 #61350 Reflect accepted cloud model selections in TUI status @bc-openai 
 #61351 Expose canonical network proxy policy patterns @viyatb-oai 
 #61352 Mark the TUI workspace as stable and enable it by default @fcoury-oai 
 #61353 Centralize TUI read-only view checks @bc-openai 
 #61354 Avoid rewriting unchanged Guardian channel descriptions @felixxia-oai 
 #61355 Upgrade Bazel rules_rs to 0.2.3 @seanh-oai 
 #61356 Add deferred MCP reprojection for the next regular turn @kchainani-oai 
 #61357 Clarify removal scope for profile MCP servers @etraut-openai 
 #61358 Add structured error kinds for exec-server process starts @andrewgu-oai 
 #61359 Resolve queued attachment paths against the thread working directory @etraut-openai 
 #61365 Limit MCP status discovery to the requested page @charliemarsh-oai 
 #61369 Use native permission profiles for diagnostics and sandbox checks @ioanbudea-OAI 
 #61370 Remove BuildBuddy presets from the checked-in Bazel configuration @hintz-openai 
 #61371 Add opt-in signer-service support for macOS releases @tarunoai 
 #61372 Add opt-in transparent TCP routing for Linux sandboxes @viyatb-oai 
 #61374 Delegate installed plugin recommendation filtering to the endpoint @zamoshchin-openai 
 #61379 Remove unused workspace entries and simplify Rust code @andrewgu-oai 
 #61380 Add cell-aware mouse selection to transcript tables @fcoury-oai 
 #61381 Update the harness provenance comment in context history @vivi 
 #61382 Make clock reads synchronous and remove client clock requests @euroelessar 
 #61383 Keep the composer responsive while opening new conversations @bc-openai 
 #61384 Support Orbit originators in model catalog partitioning @bromano-oai 
 #61385 Add configurable idle heartbeats to Code Mode gRPC streams @surajs-oai 
 #61386 Reuse cloud plugin catalogs across turns until invalidated @TAFOYA-OAI 
 #61387 Refresh plugin recommendations when tooling state changes @zamoshchin-openai 
 #61388 Include the Windows sandbox service in release builds @zm-oai 
 #61389 Reduce session submission channel memory with boxed payloads @charliemarsh-oai 
 #61390 Preserve active additional context across compaction @dylan-hurd-oai 
 #61391 Normalize managed network requirements before merging @viyatb-oai 
 #61393 Add optional release IDs to cloud plugin source locations @zamoshchin-openai 
 #61394 Add opt-in file-backed tool audio @hung-oai 
 #61395 Remove legacy sandbox-policy accessors from configuration @ioanbudea-OAI 
 #61397 Add default model provider selection to the app server @abhinav-oai 
 #61398 Restore shared connector metadata for Codex Apps tools @mzeng-openai 
 #61400 Retry incomplete cloud catalogs with exponential backoff @TAFOYA-OAI 
 #61401 Release MCP OAuth read locks before keyring access @celia-oai 
 #61402 Update Daybreak links in TUI cybersecurity notices @jamy-OAI 
 #61403 Add a structured status-line snapshot for the displayed thread @joesavona 
 #61405 Show the primary executor's workspace in TUI status surfaces @joesavona 
 #61408 Expose token usage totals in statusline state @joesavona 
 #61409 Expose context usage in statusline state @joesavona 
 #61410 Expose thread costs in statusline state and reject stale usage reads @joesavona 
 #61411 Ignore stale workspace headline requests and archived messages @joesavona 
 #61415 Expose the workspace headline in structured status-line state @joesavona 
 #61417 Expose Codex rate limits in statusline state @joesavona 
 #61418 Require a government workspace for the government backend @jackz100 
 #61419 Resolve pasted Windows paths with wslpath in WSL @etraut-openai 
 #61420 Clear the user endpoint override during GCP setup @alexsong-oai 
 #61421 Use thread-scoped model catalogs for model lookups @abhinav-oai 
 #61422 Add keyboard table selection to the transcript @fcoury-oai 
 #61424 Refill the transcript viewport when collapsing tool groups @fcoury-oai 
 #61426 Enable incremental tools by default for Amazon Bedrock @akira-oai 
 #61428 Require OAuth CONNECT metadata for Portals TCP tunnels @apanasenko-oai 
 #61429 Refresh cloud plugin and skill catalogs during step preparation @TAFOYA-OAI 
 #61430 Instrument MCP OAuth credential store locks @celia-oai 
 #61434 Close abandoned tool dispatch traces as aborted @maxj-oai 
 #61437 Avoid starting dormant REPL servers for cleanup hooks @dob-oai 
 #61438 Use the provider default RPC in the TUI @abhinav-oai 
 #61444 Add process-local launch directories for shared MCP servers @charliemarsh-oai 
 #61446 Add thread ID inclusion filters to thread/list @btraut-openai 
 #61449 Add explicit cloud catalog refresh before turn admission @TAFOYA-OAI 
 #61452 Add optional tool output rendering for context window hints @euroelessar 
 #61461 Refactor session mail recording and compaction metadata capture @euroelessar 
 #61465 Move JSON byte counting into codex-utils-string @euroelessar 
 #61473 Persist timestamped realtime frames before acknowledging completion @zahan-oai 
 #61480 Add snapshot pagination for persisted realtime history @zahan-oai 
 #61481 Allow Ctrl+C to quit during Cloud session switches @bc-openai 
 #61486 Keep archived threads read-only and support unarchiving in the TUI @bc-openai 
 #61488 Harden Git remote collection and limit remote URL metadata @ningyi-oai 
 #61490 Preserve the current Cloud task until navigation is ready @bc-openai 
 #61494 Describe context and permissions per environment behind a feature flag @sayan-oai 
 #61535 Add trusted request-country metadata to Responses requests @goodman-oai 
 #61562 Unify model request hook lifecycles across sampling and compaction @tz-openai 
 #61577 Add response processing after completion and usage accounting @tz-openai 
 #61578

[... truncated for safety ...]

</details>