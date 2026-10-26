---
id: inbox_ee41b7c7
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0346-codex-releases-0-164-0-9d3d]]"
title: "0.164.0"
url: https://github.com/openai/codex/releases/tag/rust-v0.164.0
source: codex-releases
published_at: 2026-10-23T04:50:58+00:00
fetched_at: 2026-10-24T03:51:18.238015+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex 0.164.0 新增可存常用 prompt 的 presets，並補強壓縮、續接與沙箱安全。 **Why** 長期使用 CLI 時，重複輸入 prompt、壓縮失敗弄壞歷史、續接丟失設定，以及沙箱路徑繞過都會影響可靠度。 **How** 提供十個編號 /presets 槽位與鍵盤選單，/model 與 /permissions 支援行內參數；壓縮失敗時不再留下殘缺摘要，續接會還原已存的 thread 設定。 **What** OpenAI Codex v0.164.0：新增 /presets、行內 /model 與 /permissions 參數、Kitty/Sixel 終端的全螢幕圖片預覽、企業 MCP 以 Codex 帳號授權或獨立登入驗證，以及遠端 Bash 與 Zsh snapshot 的憑證遮罩。Amazon Bedrock 設定精靈預設啟用；macOS 大小寫變體 metadata 路徑與可替換 symlink 的沙箱檢查被加固，Windows proxy 支援 Negotiate/NTLM 驗證，並改善磁碟用量與 V8 升級至 152.2.0（Array.sort 安全防護）。"
key_points:
  - "新增 /presets：十個編號槽位儲存可重用 prompt 與 slash command，並有鍵盤選單；/model 與 /permissions 支援行內設定模型、reasoning effort、速度與權限 profile"
  - "安全強化：遠端 Bash 與 Zsh snapshot 憑證遮罩、macOS 大小寫變體 metadata 路徑與可替換 symlink 的沙箱檢查"
  - "穩定性修正：壓縮失敗不再留下殘缺摘要、續接可找到壓縮歷史並還原 thread 設定、Windows proxy 支援 Negotiate/NTLM"
tags: [openai-codex, release-notes, presets, sandbox, mcp]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## 0.164.0

OpenAI Codex 0.164.0 新增可存常用 prompt 的 presets，並補強壓縮、續接與沙箱安全。

**Why** 長期使用 CLI 時，重複輸入 prompt、壓縮失敗弄壞歷史、續接丟失設定，以及沙箱路徑繞過都會影響可靠度。

**How** 提供十個編號 /presets 槽位與鍵盤選單，/model 與 /permissions 支援行內參數；壓縮失敗時不再留下殘缺摘要，續接會還原已存的 thread 設定。

**What** OpenAI Codex v0.164.0：新增 /presets、行內 /model 與 /permissions 參數、Kitty/Sixel 終端的全螢幕圖片預覽、企業 MCP 以 Codex 帳號授權或獨立登入驗證，以及遠端 Bash 與 Zsh snapshot 的憑證遮罩。Amazon Bedrock 設定精靈預設啟用；macOS 大小寫變體 metadata 路徑與可替換 symlink 的沙箱檢查被加固，Windows proxy 支援 Negotiate/NTLM 驗證，並改善磁碟用量與 V8 升級至 152.2.0（Array.sort 安全防護）。

### 重點
- 新增 /presets：十個編號槽位儲存可重用 prompt 與 slash command，並有鍵盤選單；/model 與 /permissions 支援行內設定模型、reasoning effort、速度與權限 profile
- 安全強化：遠端 Bash 與 Zsh snapshot 憑證遮罩、macOS 大小寫變體 metadata 路徑與可替換 symlink 的沙箱檢查
- 穩定性修正：壓縮失敗不再留下殘缺摘要、續接可找到壓縮歷史並還原 thread 設定、Windows proxy 支援 Negotiate/NTLM

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/rust-v0.164.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New Features 
 
 Save reusable prompts and slash commands in ten numbered /presets slots, with a keyboard menu for quick access. ( #54380 , #54381 ) 
 Set model, reasoning effort, speed, and permission profiles directly with inline /model and /permissions arguments. ( #54378 , #54383 ) 
 Preview viewed and generated images in the fullscreen transcript on terminals supporting Kitty or Sixel graphics. ( #54216 ) 
 Authenticate enterprise MCP connections using eligible Codex account grants or dedicated sign-in, including OAuth clients requiring secrets. ( #55334 , #55859 , #56001 ) 
 Mask credentials during supported remote Bash commands and Zsh snapshot sessions, including credentials from custom providers. ( #54309 , #54432 , #56049 ) 
 The Amazon Bedrock setup wizard is now enabled by default, with API key entry grouped alongside other AWS sign-in methods when credentials are detected. ( #56033 , #56023 ) 
 
 Bug Fixes 
 
 Failed compaction no longer leaves partial summaries in conversation history, and background compaction failures fall back without panicking. ( #53932 , #55581 ) 
 Resuming sessions now finds compressed histories and restores saved thread settings instead of replacing them with global defaults. ( #54008 , #55923 ) 
 Windows HTTPS and WebSocket connections now handle proxy authentication challenges using the signed-in user’s Negotiate or NTLM credentials. ( #55994 , #56000 ) 
 CLI configuration overrides are preserved when -c or --config appears at multiple subcommand levels. ( #56022 ) 
 Queued prompts now wait for pending permission selections to resolve before continuing. ( #55682 ) 
 Hardened sandbox checks for case-variant metadata paths on macOS and replaceable symlinks used to locate executables. ( #54273 , #55384 ) 
 
 Chores 
 
 Reduced disk usage by pruning unused installations, cleaning abandoned marketplace checkouts, and bounding daemon logs. ( #53827 , #55149 , #55689 , #55690 , #55856 ) 
 Updated the embedded JavaScript runtime with safety checks for optimized Array.sort operations. ( #54519 ) 
 
 Changelog 
 Full Changelog: rust-v0.163.0...rust-v0.164.0 
 
 #53725 Render Markdown web links as labels in Rex @bc-openai 
 #53728 Preserve the remote cwd filter in the in-app resume picker @fcoury-oai 
 #53732 Reuse compiled search patterns across compressed rollouts @ethernetdan-openai 
 #53733 Default Guardian v2 async classification to conversation mode @felixxia-oai 
 #53736 Acquire and cache opt-in executor capability inventories via V2 @TAFOYA-OAI 
 #53745 Remove modelSlug from the latest-model resolver output @kkahadze-oai 
 #53747 Prefer remote Visualize installs over the bundled plugin @philipp-oai 
 #53751 Apply feature overrides when restarting the app-server daemon @jif-oai 
 #53753 Extend copy-on-select to composer text @fcoury-oai 
 #53754 Support Command/Super shortcuts in the TUI keymap @fcoury-oai 
 #53763 Enrich V2 capability discovery with resolved plugin and skill metadata @TAFOYA-OAI 
 #53780 Remove redundant Codex manual cache directory check @kkahadze-oai 
 #53781 Remove the product-gating TODO from SkillPolicy @kkahadze-oai 
 #53784 Forward client voice session IDs in realtime requests @chrisdong-oai 
 #53790 Fix cancellation of macOS user-verification prompts @bz-openai 
 #53794 Retain rollout migration locks across worker cancellation @jif-oai 
 #53795 Use the bundled model catalog in the MCP startup invalidation test @OLI-OAI 
 #53797 Refresh Guardian reviews when review context changes @jif-oai 
 #53800 Wire background compaction into the turn lifecycle @rka-oai 
 #53804 Keep the Agent command center visible during archive and delete @etraut-openai 
 #53805 Add safe diagnostics to workspace routing configuration errors @etraut-openai 
 #53811 Support daemon installation from Windows WinGet packages @etraut-openai 
 #53816 Reject Guardian review threads during interactive CLI resume @dylan-hurd-oai 
 #53827 Prune unused app-server daemon releases safely @etraut-openai 
 #53831 Track content provenance through prompt assembly and compaction @tz-openai 
 #53845 Fix daemon updater socket binding and bootstrap readiness on Unix @etraut-openai 
 #53853 Reuse staged file digests when preparing daemon installs @charliemarsh-oai 
 #53859 Record bucketed terminal sizes in TUI telemetry @imac-oai 
 #53872 Refresh model instructions in incremental-tool context windows @rhan-oai 
 #53879 Preserve running turn recovery across thread settings updates @bc-openai 
 #53895 Resume unloaded subagent threads when selected in the TUI @etraut-openai 
 #53897 Isolate daemon package tests to reduce disk contention @etraut-openai 
 #53908 Keep the agent dashboard browsable during task removal @etraut-openai 
 #53932 Preserve conversation history when compaction fails @jif-oai 
 #53940 Bound rollout input for memory extraction @jif-oai 
 #53947 Stop rollout reads when the calling task is cancelled @jif-oai 
 #53963 Test memory extraction budgets with excluded items and ciphertext @jif-oai 
 #53969 Avoid reconnect races in the daemon restart test @jif-oai 
 #53987 Skip service backoff for stale Guardian authorization retries @jif-oai 
 #53990 Keep host MCP and plugin configuration local with remote environments @jif-oai 
 #53991 Report the reason for ChatGPT token refresh requests @tejsudha-openai 
 #53996 Bump rustls to 0.23.46 @jif-oai 
 #53997 Filter rollout filenames before checking compressed siblings @bbrown-oai 
 #54003 Include compressed rollouts in doctor storage statistics @jif-oai 
 #54008 Fix session lookup and resume after rollout compression @jif-oai 
 #54027 Preserve Windows startup variables and MXC child environment defaults @iceweasel-oai 
 #54032 Bound concurrent Git diffs for untracked files @yuzhu-oai 
 #54033 Extend memory extension resource retention to 14 days @josh-oai 
 #54039 Return async Guardian approvals before review cleanup finishes @jif-oai 
 #54044 Keep fork lineage ahead of paginated transcript history @fcoury-oai 
 #54046 Track approval cancellation sources and Guardian context changes @vkg-oai 
 #54047 Restore elapsed time for replayed in-progress turns @etraut-openai 
 #54048 Defer folder trust checks until starting a task from agents overview @etraut-openai 
 #54050 Scope TUI skill refreshes and workspace commands to explicit directories @etraut-openai 
 #54053 Add Responses API client metadata patches for turn start and steer @marksteinbrick-oai 
 #54056 Coalesce overlapping native TLS root certificate loads @jif-oai 
 #54057 Distinguish unsupported evidence in Decisions comparison metrics @swastik-oai 
 #54058 Forward turn metadata to image generation and edit requests @duc-openai 
 #54059 Support store-owned preparation when resuming threads @owenlin0 
 #54060 Limit unarchive scans to the requested thread's archived rollouts @bz-openai 
 #54069 Fix Windows environment handling for remote MCP servers @iceweasel-oai 
 #54070 Expose gateway authentication as a reusable OAuth session API @smurching-oai 
 #54076 Avoid false URL-launch detections in literal PowerShell commands @jif-oai 
 #54078 Update gix to 0.89.0 and gix-url to 0.40.0 @jif-oai 
 #54079 Retire rejected MCP OAuth refresh tokens @mzeng-openai 
 #54080 Extract TUI user-turn submission into a dedicated module @bc-openai 
 #54081 Centralize vertical navigation in TUI list views @bc-openai 
 #54082 Stabilize the Guardian network review timeout test @felixxia-oai 
 #54087 Upgrade Bazel's rules_python to 2.4.2 @dkovalenko-oai 
 #54094 Preserve specific MCP failure codes in metrics and spans @TAFOYA-OAI 
 #54096 Add Bazel targets for on-demand schemas and Python SDK generation @dkovalenko-oai 
 #54097 Show Daybreak notices after the session header @charliemarsh-oai 
 #54098 Keep environment tools stable across readiness changes @aibrahim-oai 
 #54099 Wait for readiness in the SIGTERM cancellation test @felixxia-oai 
 #54113 Embed generated app-server schema bundles in Bazel builds @dkovalenko-oai 
 #54114 Report terminal completion states and blocking reasons @cconger 
 #54119 Allow stdin review under active grants with sandbox prompts disabled @tepman-oai 
 #54133 Record per-tool incremental update and description size metrics @akira-oai 
 #54135 Allow large file writes over direct exec-server WebSockets @ostepanian 
 #54151 Generate keymap descriptors and binding accessors from one catalog @bc-openai 
 #54169 Reload the model catalog after account changes @smurching-oai 
 #54170 Preserve ChatGPT authentication for Gov MCP servers @lsingh-oai 
 #54175 Retire worktree and voice feature flags @bc-openai 
 #54216 Show image previews in the fullscreen transcript @etraut-openai 
 #54217 Apply syntax theme colors to Markdown prose in the TUI @etraut-openai 
 #54250 Add regression tests for case-variant metadata protection @jif-oai 
 #54257 Preserve recent speech when trimming realtime transcripts @jif-oai 
 #54263 Require fresh Guardian approval for escalated tool retries @jif-oai 
 #54264 Track Guardian transcript admission across failed reviews @jif-oai 
 #54265 Add regression coverage for Guardian sandbox retry approvals @jif-oai 
 #54273 Protect metadata writes through macOS case aliases @jif-oai 
 #54278 Share Guardian image deduplication and checkpoint restoration @felixxia-oai 
 #54281 Attribute compaction summaries to the assistant in Guardian transcripts @jif-oai 
 #54309 Enable credential masking for remote exec-server commands @viyatb-oai 
 #54315 Keep TUI Markdown colors readable against their backgrounds @fcoury-oai 
 #54316 Centralize context fragment kind constants @ioanbudea-OAI 
 #54346 Add scoped executor credential auth for remote exec-server @viyatb-oai 
 #54351 Use the turn index for turn-scoped item pagination @bz-openai 
 #54363 Filter uninspectable network roots from implicit MXC read grants @iceweasel-oai 
 #54365 Prevent duplicate assistant messages around interleaved commands @fcoury-oai 
 #54369 Retry SQLite operations on transient writer contention @willwang-openai 
 #54378 Support inline model, reasoning, and speed selection in /model @fcoury-oai 
 #54379 Add configuration support for TUI input presets @fcoury-oai 
 #54380 Add /presets for reusable prompts and slash commands @fcoury-oai 
 #54381 Add a keyboard shortcut menu for presets @fcoury-oai 
 #54383 Support inline permission profile selection with /permissions @fcoury-oai 
 #54385 Allow saving current permission settings as presets @fcoury-oai 
 #54387 Add session-only arguments to /title and /statusline @fcoury-oai 
 #54388 Add quick dial presets for terminal title and status line layouts @fcoury-oai 
 #54389 Preserve existing SQLite journal modes on startup @dkovalenko-oai 
 #54398 Store generated image items as attachment references @kchainani-oai 
 #54401 Run managed daemon processes at background priority on macOS @bc-openai 
 #54414 Allow root turn suspension with live descendants @miz-openai 
 #54417 Skip SQLite page reclamation on Linux NFS mounts @dkovalenko-oai 
 #54419 Support line breaks in Mermaid flowchart node labels @etraut-openai 
 #54420 Record local image inputs on completed image-generation items @mjkaufer-openai 
 #54421 Treat explicit connections to the verified default daemon as local @etraut-openai 
 #54424 Add remote plugin metadata to plugin configuration @mzeng-openai 
 #54432 Support remote credential masking with Zsh shell snapshots @viyatb-oai 
 #54433 Use neutral labels for nonzero exits in compact TUI output @bc-openai 
 #54434 Add rotating stdin credentials for remote exec-server @viyatb-oai 
 #54445 Remove obsolete protected-path monitoring from the Linux sandbox @viyatb-oai 
 #54475 Use a synchronous mutex for remote metadata request tracking @anp-oai 
 #54505 Add streaming file replacement to filesystem abstractions @anp-oai 
 #54519 Upgrade V8 to 152.2.0 and backport Array.sort safety guards @seanh-oai 
 #54589 Preserve evidence message structure in Guardian Decisions requests @swastik-oai 
 #54590 Capture sender context for codex

[... truncated for safety ...]

</details>