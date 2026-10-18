---
id: inbox_236c8dba
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.39.0"
author: "thedotmack"
published_at: 2026-10-13T21:31:41+00:00
fetched_at: 2026-10-18T02:56:55.888284+00:00
content_hash: "535911e12fe97888bda791d49394b06b968a33c348531cf4ec73b84a859c7385"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.39.0

Codex: memory timeline returns to subagent threads after compaction 
 When Codex compacts a thread, the memory timeline drops out of its history. The root thread already got it back through SessionStart (source compact ). Codex never sends SessionStart to subagent threads, though, so a subagent that compacted kept working without its memory. 
 
 A new PostCompact hook marks the compacted thread, keyed by session_id plus agent_id . 
 That thread's next PostToolUse records the observation as usual, consumes the marker, and returns the timeline once as additionalContext . 
 SessionStart clears the marker, so the root thread never gets the timeline twice. 
 Shared session-marker file handling now backs both the Codex compaction gate and the Kimi context gate. 
 
 PR: #4733