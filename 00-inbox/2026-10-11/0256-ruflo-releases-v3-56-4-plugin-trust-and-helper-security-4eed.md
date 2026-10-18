---
id: inbox_a5e6b2f0
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.56.4"
author: "ruvnet"
published_at: 2026-10-11T01:08:38+00:00
fetched_at: 2026-10-18T02:56:54.702223+00:00
content_hash: "4eedcc274e2bfd47a9044777782fce046b50f5805fb65b3c26067620248b0f96"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.56.4 — plugin-trust and helper security hardening, MCP/task fixes

Patch release: plugin-trust and helper security fixes, MCP/task fixes, Node 24 sqlite fix. 
 Published: @claude-flow/cli, claude-flow, ruflo 3.56.4 (latest, alpha, v3alpha); leaves memory 3.0.4, integration 3.0.1, plugins 3.0.2, mcp 3.1.1, security 3.0.4. 
 Security: placeholder (all-zero) registry trust anchor no longer vouches ( #3948 ); plugins upgrade no longer bypasses the install gate ( #3951 ); plugin/helper locators stop at node_modules ( #3986 ); session helper path and module-root hardening ( #3949 ); helper CLI runs from the helper root, no shell interpolation of HELPER_ROOT ( #3990 ); user-level settings pin home helpers ( #3952 ); task_assign rejects proto ids ( #3967 ). 
Fixes: Node 24 better-sqlite3 abort ( #3955 ); agentic-flow root import runs its CLI ( #3958 ); MCP resource cache stale writes fenced ( #4019 ); security scan code-pattern false positives ( #3999 ); MCP/task/CLI fixes #3975 #3974 #3970 #3969 #3968 #3980 #3947 ; graph path search ~94x faster ( #3977 ). 
 Full list: CHANGELOG.md.