---
id: inbox_0f771136
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.38.0"
author: "thedotmack"
published_at: 2026-10-13T18:36:36+00:00
fetched_at: 2026-10-18T02:56:55.888833+00:00
content_hash: "db77c0d55be5dbca9db910afbe01e0f62bc085e893ab31fd417e3ab998abc3d9"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.38.0

No more console window flashing on Windows. Every Claude Code hook now calls claude-mem directly instead of going through bash, and this release also carries 16 community fixes from five contributors. 
 Hooks call claude-mem directly ( #4345 ) 
 Every Claude Code runtime hook now runs a small claude-mem launcher in exec form ( "command": "claude-mem", "args": [...] ), with no shell in between. On Windows that ends the console window that used to flash and steal focus on every tool call ( #3605 , #3559 , #3521 , #3396 , #3248 ). 
 
 npx claude-mem install / update compile the launcher on your machine. It goes to ~/.local/bin/claude-mem on macOS and Linux, or %LOCALAPPDATA%\claude-mem\bin\claude-mem.exe on Windows, and that folder is added to your PATH if it isn't there already. npx claude-mem uninstall removes the launcher. 
 Marketplace-only installs repair themselves. A startup step places or refreshes the launcher and tells you when Claude Code needs a restart. 
 The launcher fails open. On any problem it prints one line, claude-mem: &lt;reason&gt;, continuing without memory , and your session carries on. 
 The environment opt-outs ( CLAUDE_MEM_DISABLE_TOOL_HOOKS , CLAUDE_MEM_DISABLE_OBSERVATION , CLAUDE_MEM_DISABLE_FILE_CONTEXT ) still take effect before anything heavy starts. 
 
 Before you upgrade: 
 
 Hooks in exec form need Claude Code 2.1.139 or newer . install and doctor warn on older versions. 
 If the launcher's folder wasn't on your PATH yet, the first session after updating will tell you to restart Claude Code from a new terminal . After that, everything works as before. 
 
 Thanks @bagr001 for testing it on Windows 11. 
 Observer and worker 
 
 Gateways that reject the thinking parameter no longer stall the observer ( #4735 , @akushonkamen ). The observer retries once without the parameter. The token-saving default is unchanged, and CLAUDE_MEM_OBSERVER_THINKING is now documented. 
 The worker no longer wedges for hours on big repos ( #4753 , @akushonkamen ). Git commands during worktree adoption now run without blocking the event loop. 
 The streamed-request idle window is configurable ( #4752 , @akushonkamen ) with CLAUDE_MEM_LLM_STREAM_IDLE_TIMEOUT_MS , for self-hosted backends with long queue waits. The default is still 90 seconds. 
 CLAUDE_MEM_DISABLE_SUMMARY=1 skips the end-of-session summary for headless or read-only runs ( #4736 , @akushonkamen ). 
 Mode prompts are validated , and a user mode file can no longer shadow a bundled mode ( #4326 ). 
 Three platform fixes ( #3851 ):
 
 manual sessions keep their platform; 
 an error-shaped response is no longer taken for a host observer; 
 Grok agents added after install are watched. 
 
 
 The Codex installer drops a dead local marketplace registration , and install fails when Codex doesn't list the plugin afterwards ( #3494 ). 
 
 Search, viewer and data, thank you @rudycelekli 
 
 Semantic search no longer breaks on empty filters ( #4754 ) or on malformed stored concept or file data ( #4750 ). It now matches keyword search. 
 The Sessions list matches project names regardless of case ( #4749 ). 
 Feed rows with the same timestamp come back in a stable newest-first order ( #4747 ). 
 Repeated prompts with their own native turn ids are no longer merged into one ( #4748 ). 
 Restoring an export keeps each prompt's native turn id ( #4751 ). 
 Deleting a project's last memories brings the welcome hint back right away ( #4742 ). 
 A corpus built without a limit gets the documented 500 observations, and limits above 100 are no longer capped at 100 ( #4746 ). 
 
 Sync and server 
 
 Chroma writes for the same memory are serialized and re-read the current row ( #4731 , @junnhwan ). A startup backfill or a delayed cloud forward can no longer index an old body or old project. 
 On the self-hosted server, a reclaimed generation attempt can't complete or fail its replacement ( #4739 , @junnhwan ). Postgres regression tests now run in CI. 
 The self-hosted sync server puts brackets around IPv6 hosts in its advertised URL ( #4723 , @DeryFerd ). 
 
 Viewer 
 
 The NOTES section icon is sized like its siblings ( #4744 , @phant0um , first contribution). It used to render about 20× too large. 
 
 Claude app (cowork) plugin 
 
 Session-init now runs in the background, and the plugin's hooks stand down when a local claude-mem install is present ( #4755 ). 
 
 Docs and skills 
 
 The make-plan skill has a Primary Goal section and a fixed short chat summary ( #3600 ). 
 The wowerpoint skill stops once the deck has started and no longer uploads ( #4342 ). 
 Docs no longer mention workers.dev for the sync hub ( #4366 ). 
 
 Thanks to everyone who reported and fixed things this round: @rudycelekli , @junnhwan , @akushonkamen , @DeryFerd , @phant0um , @valerianbbragi , @smashingtags , @wuding129 , @chris-yyau , @bagr001 . 
 Full diff: v13.37.0...v13.38.0