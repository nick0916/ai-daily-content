---
id: inbox_b512d4df
date: 2026-10-11
source_ref: "[[00-inbox/2026-10-11/0256-ruflo-releases-v3-56-7-ruflo-tui-mcp-resources-auto-mem-3a8f]]"
title: "v3.56.7 — ruflo tui, MCP resources, auto-memory and purge fixes, safer init --dual"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.56.7
source: ruflo-releases
published_at: 2026-10-11T22:53:31+00:00
fetched_at: 2026-10-18T03:20:23.510124+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 發布 v3.56.7 功能型 patch（@claude-flow/cli、claude-flow、ruflo），並獨立發布 @claude-flow/codex 3.0.4（CLI 以精確版本 pin）。最大新增是 `ruflo tui`：把 ruflo console 放進獨立終端（ADR-489，#4059、#4075、#4076），共六頁（Overview、Cost、Swarm、Events、Missions 唯讀，以及 AI 頁），可用 `--view` 或按鍵 1-6 開啟；AI 頁可詢問 Codex（pin 0.162.0、唯讀）或 OpenRouter，每次提問前都有 confirm card。`--no-ai` 可關閉 AI 頁，`--max-spend-usd`（預設 0.5）在 OpenRouter 回報花費達上限後停止送出；`--plain` 印出單一畫面並以 0 結束，無終端時以 2 結束並附提示。CLI tarball 現含約 1.27 MB（gzip 後 446 KB）的 tui.mjs，整體 tarball 約 3.9 MB。其他新增：CLI server 支援 MCP resources capability，並建立 Claude Code / Codex / OpenRouter 三 host 整合迴圈（ADR-490/491，#4068）；doctor 會標示在 Node 24.19–24.21 上以 24.19+ headers 建置的 better-sqlite3（#4069、#4074）；`ruflo mods` 新增 doctor repair、`--strict`、atomic install 與啟動自檢（#4073）。修正包括 auto-memory hooks、worktree 共用主 memory 目錄、store 寫入原子化（#4071、#4058），以及 memory purge 在 sql.js write-back 時保留磁碟格式（#4057）。行為變更：`init --dual` 現在寫入安全的預設 `.codex/config.toml`，舊的寬鬆值需用 `--codex-trust full`（#4070）。已知問題：agentdb 與 agentic-flow 下仍有巢狀 better-sqlite3 11.x，需等 agentdb 改依賴 ^12 才能修。"
key_points:
  - "`ruflo tui` 六頁介面，AI 頁每次提問需 confirm card，`--max-spend-usd` 預設 0.5 做 OpenRouter 花費上限；Codex 固定 pin 0.162.0 且唯讀"
  - "`init --dual` 預設改寫安全的 .codex/config.toml，舊的寬鬆設定須明確加 `--codex-trust full`"
  - "doctor 新增檢查：Node 24.19–24.21 上以 24.19+ headers 建置的 better-sqlite3；巢狀 better-sqlite3 11.x 仍待 agentdb 升到 ^12"
tags: [ruflo, tui, mcp-resources, codex, spend-cap]
topics: [agents.coding_agents, agents.mcp, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.56.7 — ruflo tui, MCP resources, auto-memory and purge fixes, safer init --dual

Ruflo 發布 v3.56.7 功能型 patch（@claude-flow/cli、claude-flow、ruflo），並獨立發布 @claude-flow/codex 3.0.4（CLI 以精確版本 pin）。最大新增是 `ruflo tui`：把 ruflo console 放進獨立終端（ADR-489，#4059、#4075、#4076），共六頁（Overview、Cost、Swarm、Events、Missions 唯讀，以及 AI 頁），可用 `--view` 或按鍵 1-6 開啟；AI 頁可詢問 Codex（pin 0.162.0、唯讀）或 OpenRouter，每次提問前都有 confirm card。`--no-ai` 可關閉 AI 頁，`--max-spend-usd`（預設 0.5）在 OpenRouter 回報花費達上限後停止送出；`--plain` 印出單一畫面並以 0 結束，無終端時以 2 結束並附提示。CLI tarball 現含約 1.27 MB（gzip 後 446 KB）的 tui.mjs，整體 tarball 約 3.9 MB。其他新增：CLI server 支援 MCP resources capability，並建立 Claude Code / Codex / OpenRouter 三 host 整合迴圈（ADR-490/491，#4068）；doctor 會標示在 Node 24.19–24.21 上以 24.19+ headers 建置的 better-sqlite3（#4069、#4074）；`ruflo mods` 新增 doctor repair、`--strict`、atomic install 與啟動自檢（#4073）。修正包括 auto-memory hooks、worktree 共用主 memory 目錄、store 寫入原子化（#4071、#4058），以及 memory purge 在 sql.js write-back 時保留磁碟格式（#4057）。行為變更：`init --dual` 現在寫入安全的預設 `.codex/config.toml`，舊的寬鬆值需用 `--codex-trust full`（#4070）。已知問題：agentdb 與 agentic-flow 下仍有巢狀 better-sqlite3 11.x，需等 agentdb 改依賴 ^12 才能修。

### 重點
- `ruflo tui` 六頁介面，AI 頁每次提問需 confirm card，`--max-spend-usd` 預設 0.5 做 OpenRouter 花費上限；Codex 固定 pin 0.162.0 且唯讀
- `init --dual` 預設改寫安全的 .codex/config.toml，舊的寬鬆設定須明確加 `--codex-trust full`
- doctor 新增檢查：Node 24.19–24.21 上以 24.19+ headers 建置的 better-sqlite3；巢狀 better-sqlite3 11.x 仍待 agentdb 升到 ^12

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.56.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Feature patch: @claude-flow/cli , claude-flow , ruflo 3.56.7 (latest, alpha, v3alpha) and @claude-flow/codex 3.0.4 (published standalone; the CLI pins it exactly). 
 Added 
 
 ruflo tui : the ruflo console in a terminal of its own (ADR-489, #4059 , #4075 , #4076 ). Six pages, opened with --view or keys 1-6: Overview, Cost, Swarm, Events, Missions (read-only) and an AI page that asks Codex (pinned 0.162.0, read-only) or OpenRouter, each question after a confirm card. --no-ai turns the AI page off; --max-spend-usd (default 0.5) stops sending to OpenRouter once provider-reported spend reaches it. --plain prints one frame and exits 0; without a terminal it exits 2 with a hint. The CLI tarball now carries the bundled plugins/ruflo-console/dist/tui.mjs (about 1.27 MB, 446 KB gzipped; tarball about 3.9 MB). Console 0.42.7 is a marketplace plugin, not npm. 
 MCP resources capability on the CLI server, and a three-host integration loop (Claude Code, Codex, OpenRouter) with ADR-490/491 ( #4068 ). 
 doctor flags a better-sqlite3 built against Node 24.19+ headers on Node 24.19-24.21 ( #4069 , #4074 ). 
 ruflo mods : doctor repairs that repair, --strict , atomic install, startup self-check ( #4073 ). 
 
 Fixed 
 
 Auto-memory hooks deliver their subcommand, sync sees learnings, worktrees share the main memory dir, store writes are atomic ( #4071 , #4058 ). 
 memory purge keeps the on-disk format on sql.js write-back ( #4057 ); command recording has an off switch and redaction, and memory cleanup --expired-only reaches the bridge store ( #4056 , #4072 ). 
 
 Changed 
 
 init --dual now writes a safe default .codex/config.toml . The old permissive values need --codex-trust full ( #4070 ). 
 
 Known 
 
 Nested better-sqlite3 11.x copies under agentdb and agentic-flow still ship. Fixing that needs an agentdb release that depends on better-sqlite3 ^12. doctor warns on affected Node versions. 
 
 Thanks 
 @ronmikailov for the reports behind the Node 24 doctor check, hook-log cleanup, memory purge format and auto-memory hook fixes ( #4055 - #4058 ); @rudycelekli for the cli-core/shared batch shipped in 3.56.6 that this train builds on; @Devesh-Maheshwari for the cost-tracker Codex usage fix ( #4048 , 3.56.6).

</details>