---
id: inbox_114801f8
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/Oct/12/web-edit/"
author: ""
published_at: 2026-10-12T15:54:36+00:00
fetched_at: 2026-10-18T02:56:33.592170+00:00
content_hash: "b4eb87aa1ddcdd8c0224c66e3e4e5d8013ccfec7dee385ee192f21e4568a3958"
lang: en
caption_quality: None
raw: true
topics: []
---

# web-edit 0.1a0

Release: web-edit 0.1a0 
 I was working on a project from my phone using Codex Remote when I found myself wanting to edit a credentials file without round-tripping those credentials through the LLM itself. 
 So... I had Codex and GPT-6 Astra Extra High build this Python web app which provides a web UI for viewing and editing files in a folder. It's intended to be run over Tailscale, so I can have an agent start this running and then edit files via my Tailscale network directly from my phone. 
 Here's the interface for browsing files in a folder: 
 
 Editing uses CodeMirror 6 - I was going to use Monaco but that still doesn't have a great mobile experience yet. 
 
 
 Tags: projects , python , ai , tailscale , generative-ai , llms , codex