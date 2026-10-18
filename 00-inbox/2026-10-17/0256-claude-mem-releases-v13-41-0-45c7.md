---
id: inbox_2818bbd7
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.41.0"
author: "thedotmack"
published_at: 2026-10-17T02:17:07+00:00
fetched_at: 2026-10-18T02:56:55.887457+00:00
content_hash: "45c77c39a33a2898928b1779c4c2dae0f4cc382bd9d69fb21b5dcd97d6aa2df9"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.41.0

Build, release, and work-state visibility 
 Workflow skills 
 
 build delegates a coding session through make-plan , do , and babysit . 
 release delegates publication through version-bump and childhood . 
 build-and-release runs both, merging the ready PR before continuing from updated main. 
 Restores the existing childhood skill so post-release verification is included. 
 
 The new wrappers are deliberately short. They reuse the existing workflows. 
 Work-state telemetry 
 Adds privacy-preserving PostHog rollups for work-state usage by release, host platform, and recorded agent role. The rollups distinguish captured reads and writes, outcomes, native to-do use, instruction handoffs, and missing attribution. 
 MCP execution receipts also cover failures before a worker responds. They are a separate observation source and must not be added to captured-call totals. 
 Instruction handoffs are measured after the platform adapter formats the model-bound output and stdout succeeds. Cached context is included; discarded context and failed output are not counted as successful handoffs. Delayed or untimestamped captures cannot inherit a later instruction handoff. 
 These are diagnostic signals, not a compliance score. Returning instructions does not prove that a host accepted them or an agent followed them, and an ordinary question may correctly require no write. 
 No task titles, prompt text, project paths, or raw session/agent IDs are sent. Existing telemetry opt-out remains in effect. This release does not backfill earlier usage. 
 Local replay deduplication lasts 30 days; older events are dropped. Public/private turn boundaries remain content-free and prevent private activity from inheriting an earlier public prompt. Hosts without verified original timestamps remain outside captured prompt/tool totals.