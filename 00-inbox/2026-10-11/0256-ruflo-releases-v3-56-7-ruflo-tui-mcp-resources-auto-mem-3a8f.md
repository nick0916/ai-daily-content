---
id: inbox_b512d4df
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.56.7"
author: "ruvnet"
published_at: 2026-10-11T22:53:31+00:00
fetched_at: 2026-10-18T02:56:54.701234+00:00
content_hash: "3a8fa47f3da925742b95f6c593b82993942c735b106e30ddaeafb0cb541bb1bf"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.56.7 — ruflo tui, MCP resources, auto-memory and purge fixes, safer init --dual

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