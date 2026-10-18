---
id: inbox_01b30c8d
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.56.6"
author: "ruvnet"
published_at: 2026-10-11T16:49:28+00:00
fetched_at: 2026-10-18T02:56:54.701609+00:00
content_hash: "d01bec1cfbb55c0cccf471dcc6ca66d89b41a4d4e3bfc3e10d603a1a9aeaaa39"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.56.6 — Windows hook launch fix, SessionStart risk scanner, cli-core/shared fixes

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.6 (latest, alpha, v3alpha). The CLI now pins @claude-flow/cli-core 3.7.1 and @claude-flow/shared 3.0.3 (published earlier today). 
 Fixed 
 
 Windows hooks launch through node -e instead of cmd /c , which started an interactive cmd that executed the hook JSON payload and created stray files ( #4045 ). Signed helpers changed and were re-signed ( #4053 ). 
 The settings.json risk scanner now runs on the automatic SessionStart hook; encoded-PowerShell matching is linear time ( #4052 , #4053 ). 
 Trajectory-end feedback is indexed even when steps were recorded ( #3662 , #4051 ). 
 cli-core 3.7.1 / shared 3.0.3: JSON memory backend, table and progress output, RVF event log and circuit breaker fixes ( #4061 ). 
 
 Plugins (no npm impact) 
 
 ruflo-cost-tracker : preserve Codex usage ownership ( #4048 ). ruflo-swarm : host-specific no-op manifest for native Codex hook discovery ( #4050 ). ruflo-adr 0.5.5. 
 
 Contributors 
 Thanks to @rudycelekli for the reviewed batch behind #4061 (PRs #4020 - #4026 , #4028 - #4030 , #4032 , #4033 , #4035 , #4037 ) and to @Devesh-Maheshwari for #4048 .