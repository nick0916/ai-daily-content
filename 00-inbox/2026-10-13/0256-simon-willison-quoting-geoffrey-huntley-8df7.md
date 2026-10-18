---
id: inbox_37d9fe9a
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Oct/13/geoffrey-huntley/"
author: ""
published_at: 2026-10-13T13:32:00+00:00
fetched_at: 2026-10-18T02:56:33.590563+00:00
content_hash: "8df791e3dde55075b60ba76ed7ca0caa0752957f8f3b30301aec257824bec2f3"
lang: en
caption_quality: None
raw: true
topics: []
---

# Quoting Geoffrey Huntley

If the agent isn't using my diagnostics library, I could introspect and update AGENTS.md, but there's still a delta, and it'll drift. Instead, I write a pre-commit hook that checks the git diff for direct calls to observability modules that bypass my diagnostics module. Boom: fail the commit, inject a prompt telling the agent to use the diagnostics library. All of a sudden it's ten out of ten. 
 &mdash; Geoffrey Huntley , nobody should type code by hand anymore. here's what's left. 

 Tags: coding-agents , generative-ai , git , agentic-engineering , ai , geoffrey-huntley , llms