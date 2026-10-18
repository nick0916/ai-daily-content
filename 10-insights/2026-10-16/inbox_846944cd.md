---
id: inbox_846944cd
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0256-claude-mem-releases-v13-40-0-eacc]]"
title: "v13.40.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.40.0
source: claude-mem-releases
published_at: 2026-10-16T12:25:04+00:00
fetched_at: 2026-10-18T03:20:52.724461+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude-Mem v13.40.0 加入 TeamBrain 終端機指令與 work-state 雲端同步，並附上大量修正。新指令 npx claude-mem teambrain join <invite-link> 以與 install 相同的 device-code 登入流程加入團隊，之後可用 status、share、leave、start（#4815）；加入團隊的成員仍保留自己的本機 observer，不會切換 observer provider。屬於團隊的安裝在 SessionStart 會加入簡短 team brief（專案內的 open collisions、近期計畫與決策、其他活躍成員、委派給你的事項），agent 另有唯讀的 team_brief 與 team_search MCP 工具。agent 的 work_state_write／work_state_read 現會以 work_state content kind 同步到雲端（伺服器啟用時），未啟用前資料留在本機不會被丟棄（#4569）。修正涵蓋 Codex hooks（bundle Zod、teardown 順序）、Search 參數驗證（INVALID_DATE、INVALID_PAGINATION，#4786、#4787）、隱私（剝除巢狀與重疊的 memory tag #4761、opt-in 的通用 credential pattern #4762）、Cursor hooks.json 保留使用者條目（#4783）等。升級注意：本機資料庫 schema 升至 v67，舊版不能開啟新版已開過的資料庫（無法降級），共用 ~/.claude-mem 的所有安裝都要更新；多機使用者需注意 v13.29.0 之前的版本無法略過不認識的 sync 內容。"
key_points:
  - "新增 teambrain join/status/share/leave/start 指令與 SessionStart team brief，並提供唯讀 team_brief、team_search MCP 工具（#4815）"
  - "work-state 以 work_state content kind 同步雲端，伺服器未啟用時資料留在本機不丟棄（#4569）"
  - "升級風險：資料庫 schema 升至 v67 且不可降級，共用 ~/.claude-mem 的所有安裝都必須更新；v13.29.0 以前版本無法略過不認識的 sync 內容"
tags: [claude-mem, teambrain, work-state-sync, mcp-tools, schema-migration]
topics: [agents.coding_agents, agents.mcp, product_and_org.product]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.40.0

Claude-Mem v13.40.0 加入 TeamBrain 終端機指令與 work-state 雲端同步，並附上大量修正。新指令 npx claude-mem teambrain join <invite-link> 以與 install 相同的 device-code 登入流程加入團隊，之後可用 status、share、leave、start（#4815）；加入團隊的成員仍保留自己的本機 observer，不會切換 observer provider。屬於團隊的安裝在 SessionStart 會加入簡短 team brief（專案內的 open collisions、近期計畫與決策、其他活躍成員、委派給你的事項），agent 另有唯讀的 team_brief 與 team_search MCP 工具。agent 的 work_state_write／work_state_read 現會以 work_state content kind 同步到雲端（伺服器啟用時），未啟用前資料留在本機不會被丟棄（#4569）。修正涵蓋 Codex hooks（bundle Zod、teardown 順序）、Search 參數驗證（INVALID_DATE、INVALID_PAGINATION，#4786、#4787）、隱私（剝除巢狀與重疊的 memory tag #4761、opt-in 的通用 credential pattern #4762）、Cursor hooks.json 保留使用者條目（#4783）等。升級注意：本機資料庫 schema 升至 v67，舊版不能開啟新版已開過的資料庫（無法降級），共用 ~/.claude-mem 的所有安裝都要更新；多機使用者需注意 v13.29.0 之前的版本無法略過不認識的 sync 內容。

### 重點
- 新增 teambrain join/status/share/leave/start 指令與 SessionStart team brief，並提供唯讀 team_brief、team_search MCP 工具（#4815）
- work-state 以 work_state content kind 同步雲端，伺服器未啟用時資料留在本機不丟棄（#4569）
- 升級風險：資料庫 schema 升至 v67 且不可降級，共用 ~/.claude-mem 的所有安裝都必須更新；v13.29.0 以前版本無法略過不認識的 sync 內容

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.40.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's new 
 TeamBrain from the terminal 
 
 npx claude-mem teambrain join &lt;invite-link&gt; connects this install to a TeamBrain team using the same device-code sign-in as install . You approve the device in the browser, then choose which projects to share. Also: teambrain status , teambrain share , teambrain leave , teambrain start . ( #4815 ) 
 Members who join with a team seat keep their own local observer — joining never switches your observer provider. 
 When an install belongs to a team, SessionStart adds a short team brief : open collisions in this project, recent plans and decisions, who else is active, and items delegated to you. Agents also get read-only team_brief and team_search MCP tools. Installs that are not in a team see no change. 
 
 Work-state sync 
 
 The agent's work-state tracker ( work_state_write / work_state_read ) now syncs to the cloud as a work_state content kind, for accounts where the sync server enables it. Until then rows wait locally — they are never dropped. Devices that skipped work-state ops on older builds apply them once after upgrading. ( #4569 ) 
 
 Also new 
 
 The Claude observer can batch queued events (opt-in). ( #4793 ) 
 Viewer: the NOTES summary section has its own icon ( #4776 ); long prompts clamp behind a "Show more" disclosure ( #4765 ). 
 
 Fixes 
 
 Codex: bundle Zod so cached hooks load without node_modules ( #4771 ); reject a host root without its dependencies in the hook resolver ( #4766 ); finish teardown before removing the private runtime ( #4792 ). 
 Search: reject an unparseable dateStart / dateEnd with 400 INVALID_DATE ( #4786 ); validate limit / offset with 400 INVALID_PAGINATION ( #4787 ); make the implicit 90-day recency window configurable ( #4773 ). 
 Privacy: strip nested and overlapping memory tags ( #4761 ); opt-in generic credential patterns, with the redaction settings documented ( #4762 ). 
 Ingest: register an unknown project when hook payloads have no cwd ( #4774 ); apply CLAUDE_MEM_SKIP_BASH_PATTERNS to the PowerShell tool ( #4756 ). 
 Hooks: skip SessionEnd for sessions that are never tracked ( #4780 ); fix hook spool delivery to remote workers ( #4626 ). 
 Worker: spare a silent worker whose liveness heartbeat is fresh, for a bounded time ( #4794 ). 
 Projects: promote a merged-from project to a read key only for whole-project merges ( #4789 ). 
 Context files: keep CLAUDE.md/AGENTS.md symlinks when refreshing context ( #4784 ). 
 Exclusions: a trailing /** pattern also excludes the directory itself ( #4785 ). 
 Cursor: preserve your own hooks.json entries on install/uninstall ( #4783 ). 
 Logger: keep the day log open instead of re-opening it per line ( #4791 ). 
 Launcher: ad-hoc re-sign the compiled binary on macOS before the protocol probe ( #4781 ). 
 CLI: show help for install , update , uninstall and other action verbs instead of running them ( #4767 ). 
 DSH: keep every table's header when collapsing duplicate rows ( #4790 ). 
 Tree-sitter: verify the CLI loads, not just that it exists ( #4777 ). 
 Build: leave posthog-node's optional OpenTelemetry import unresolved ( #4795 ). 
 
 Upgrade notes 
 
 The local database schema moves to v67 on first open. Older builds refuse a database a newer build has opened (no downgrade), so update every install that shares ~/.claude-mem . 
 If work-state sync is enabled for your account, your existing work-state history uploads once. 
 Using claude-mem on more than one machine? Update all of them — builds older than v13.29.0 cannot skip sync content they don't recognize.

</details>