---
id: inbox_b1e513c8
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.36.1"
author: "thedotmack"
published_at: 2026-10-12T21:01:07+00:00
fetched_at: 2026-10-18T02:56:55.889660+00:00
content_hash: "eab035222031606e1c1353162eb9cbfc7cd57d1e3816c3a0f6c793b669b8cbe0"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.36.1

A patch release that closes three issues found in review of 13.36.0, plus eight community fixes. Upgrading is recommended. 
 Privacy and data safety 
 
 &lt;private&gt; content no longer leaves the hook in server runtime ( #4721 ). In server runtime, file edits, tool inputs and outputs, and session-start prompts were sent to the server with &lt;private&gt; sections still inside, and the server kept them in the raw event record (they were removed only later, when the model prompt was built). Private sections are now removed before anything leaves the hook, and the server removes them again before it stores events or session metadata. Worker runtime (the default) was not affected. 
 Older and newer workers can no longer race on a database upgrade ( #4724 ). The check that stops an older claude-mem from opening a database a newer version upgraded now reads and records the schema writer inside one SQLite write lock, before any migration runs. Before, two workers opening the database at the same moment could both pass the check. 
 A cancelled Chroma connection can no longer release a newer connection's lock ( #4722 ). Each Chroma connection now owns its writer-lock token and releases only that lock, so a reconnect during shutdown can't leave the new sidecar unlocked and allow a second writer on the same store. Process-table parsing for the orphan sweep now has fixture tests. 
 
 Community fixes — thank you @rudycelekli 
 
 Integration ids such as constructor no longer resolve through the alias table ( #4712 ) 
 Postgres numeric settings accept only whole positive numbers; values like 5ms fall back to the default ( #4713 ) 
 Gemini retry hints too large to represent are ignored, so a key isn't parked indefinitely ( #4714 ) 
 The billing-type file is read correctly when it starts with a UTF-8 BOM ( #4715 ) 
 API-key settings arrays keep only string entries ( #4716 ) 
 A malformed part in a Gemini response no longer discards the whole answer ( #4717 ) 
 Refused connections are recognized inside wrapped errors, so recovery kicks in ( #4718 ) 
 Hook launchers honor the environment opt-out flags before starting Node or Bun ( #4719 ) 
 
 Full diff: v13.36.0...v13.36.1