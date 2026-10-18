---
id: inbox_d5108b0f
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.294"
author: "ashwin-ant"
published_at: 2026-10-08T05:03:54+00:00
fetched_at: 2026-10-18T02:56:31.157041+00:00
content_hash: "2979565ba61ba7062d6e56195a65010242ae3fd65a3b8cbbea3e78c6d74ab5f3"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.294

What's changed 
 
 Fixed prompt and agent hooks written as instructions (such as "Block commands that...") allowing what they should block 
 Improved how prompt hooks on Stop and SubagentStop written as instructions (such as "Carry on if the build is broken") are judged, so Claude is less likely to stop early