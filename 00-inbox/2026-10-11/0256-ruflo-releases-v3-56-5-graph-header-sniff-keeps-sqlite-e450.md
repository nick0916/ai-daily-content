---
id: inbox_f01a6d63
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.56.5"
author: "ruvnet"
published_at: 2026-10-11T02:13:43+00:00
fetched_at: 2026-10-18T02:56:54.701880+00:00
content_hash: "e4500b4fbb9aa39341ed52488174c9e2b24d66b9f41785dd584ca2941b92442d"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.56.5 — graph header sniff keeps SQLite locks

Patch release: one fix in @claude-flow/cli. 
 
 The graph-edge-writer encryption-header sniff no longer closes the raw DB file descriptor, which dropped live SQLite POSIX locks; the header is read in a bounded child process ( #4044 , fixes #4040 ). 
 
 Published: @claude-flow/cli, claude-flow, ruflo 3.56.5 (latest, alpha, v3alpha). No leaf package changed since 3.56.4.