---
id: inbox_5079f290
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.37.0"
author: "thedotmack"
published_at: 2026-10-13T03:07:09+00:00
fetched_at: 2026-10-18T02:56:55.889243+00:00
content_hash: "ba1aef76c44cc6a274c7905f722bc2046f68077fc8f8c9705df5e9fbfd84807a"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.37.0

This release fixes the broken 13.36.1 marketplace update. After that update, the worker, the MCP search server and the server runtime failed to start, so memory capture stopped. Upgrading is strongly recommended. 
 Fixes 
 
 claude-mem starts again after the 13.36.1 marketplace update ( #4728 , #4729 ). A change merged after the 13.36.1 release committed the built plugin files with leftover git stash conflict markers. The plugin installs from main , so auto-updated installs got those files under the same 13.36.1 version number. The worker failed with error: Unexpected &lt;&lt; , mcp-search closed its connection, and memory capture stopped once the older worker exited. The files are now rebuilt from clean source. The npm package claude-mem@13.36.1 was published before that change and was not affected. Thank you @nashsibanda for the rebuild and @hirohisatanigawa for the detailed report. 
 Worker startup waits out a locked database instead of failing ( #4725 ). The schema-writer check added in 13.36.0 ran before the connection's busy timeout was set. A worker starting while another process was opening the same database failed in about 1 ms with database is locked , and after two failures it was not restarted. The check now waits for the lock. 
 
 Changed 
 
 Memory keeps capturing on your Anthropic plan when your selected provider can't serve ( #4727 ). CLAUDE_MEM_QUOTA_FALLBACK_PROVIDER now defaults to claude . Settings files that saved "" get the new default too. The fallback now also covers a provider that is still rate limited or over capacity after its retries, is down, or returns the same batch twice with no usable output. Claude is used only when a Claude Code login or an Anthropic key is available. Memory moves back to your provider once it answers again. To wait for your provider instead, set CLAUDE_MEM_QUOTA_FALLBACK_PROVIDER to off . 
 
 Release safety 
 
 CI now checks the committed plugin files before it rebuilds them. It fails on merge-conflict markers anywhere in plugin/ and runs node --check on every committed plugin script ( #4729 ). Before this, CI rebuilt the bundles first and tested the rebuilt copies, which hid the broken committed ones. 
 
 If you used the 13.35.0 workaround 
 If you followed the workaround in #4728 (auto-update turned off and the plugin pinned to 13.35.0), turn autoUpdate back on for the thedotmack marketplace and restart Claude Code to move to 13.37.0. 
 Full diff: v13.36.1...v13.37.0