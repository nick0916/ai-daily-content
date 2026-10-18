---
id: inbox_fe337885
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.36.0"
author: "thedotmack"
published_at: 2026-10-12T18:12:46+00:00
fetched_at: 2026-10-18T02:56:55.890204+00:00
content_hash: "8ca3e60047d2570a45343b2477b3e03db23501a9fa455057e43629ddb02d6acd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.36.0

A community release: nearly every change since v13.35.0 came from outside contributors and is merged under their own name. Thank you all. 
 Highlights 
 
 Memories are no longer dropped when the provider says no. An empty Anthropic credit balance, an organization blocking subscription access, or a local model server that is down now pauses the observer and keeps the work instead of discarding it ( @Mola-maker ). When the observer stream ends early, its batch is handed back for reprocessing ( @shantanukhanwalkar ). 
 Windows home folders with non-ASCII names work again. Bun and Claude are found when your user folder name contains Korean, Japanese or other non-ASCII characters ( @akushonkamen ). 
 Hooks don't report your project's tsconfig as errors. This affected React Native and Expo projects ( @Totopo27 ). 
 The viewer saves only what you changed, so an old settings tab can't undo a change you made elsewhere ( @Cassian433 ). 
 Search improvements: 
 
 Correct paging ( @junnhwan ). 
 Chinese, Japanese, Korean and Thai words are found inside sentences ( @rudycelekli ). 
 Long natural-language queries fall back to any-term matching when no memory matches every word ( @devkancheti4-design ). 
 
 
 Chroma reliability: 
 
 No more stalls after a reboot on large stores ( @akushonkamen ). 
 Orphaned chroma-mcp processes that hold your data directory are cleaned up safely before starting, so they no longer cause lock fights ( @akushonkamen ). 
 
 
 
 New 
 
 Qoder plugin support ( @shouldnotappearcalm ). 
 Screenpipe skill for searching meeting and screen history and saving it to memory ( @EzraEllette ). 
 Atlas Cloud preset for the OpenAI-compatible provider ( @binyangzhu000-sudo ). 
 CLAUDE_MEM_OPENROUTER_TEMPERATURE setting ( @aeneasr ). 
 CLAUDE_MEM_SEMANTIC_INJECT_FORMAT=index : compact per-prompt memory injection ( @ktdrv ). 
 CLAUDE_MEM_WORK_STATE_ENABLED=false to turn off the work-state to-do rule ( @noesis-bot ). 
 CLAUDE_MEM_TOOL_USES_RETENTION_DAYS : opt-in pruning of the raw tool log. The default keeps everything ( @Montinou ). 
 Duplicate review: record a "distinct" or "dismissed" verdict on duplicate candidates ( @Montinou ). 
 Viewer: a Claude auth method control in settings ( @akushonkamen ). 
 Server runtime: idempotent memory uploads ( @escooterclinic ). 
 
 Fixes 
 
 Capture and sessions: 
 
 Original capture timestamps are kept for delayed events ( @junnhwan ). 
 Stale session-end events are retired ( @akushonkamen ). 
 Warnings are logged before queued work is discarded ( @Boulea7 ). 
 Tool calls whose input is null are captured, logging recovers when the log folder appears later, and every shutdown step runs ( @rudycelekli ). 
 Search triggers are restored after database upgrades ( @akushonkamen ). 
 Fewer SQLite warnings on macOS ( @CCCLL ). 
 
 
 Database safety: the database records the newest schema version that has written to it, and an older claude-mem refuses to open a database a newer one has upgraded ( @akushonkamen ). 
 Memory import and notes: 
 
 Restored memories attach to existing sessions ( @junnhwan ). 
 Native note revisions survive title dedup ( @junnhwan ). 
 Explicit notes keep their platform source in the search index ( @junnhwan ). 
 Notes that start with ---- are no longer mangled ( @akushonkamen ). 
 
 
 Search robustness: malformed file lists, plain-text concepts, folder search against absolute paths, consistent date parsing, and better patterns for native search commands ( @rudycelekli ). 
 Installers and integrations: 
 
 Cursor configs with a BOM and commented Codex TOML are read correctly, and npm can no longer hang the installer ( @rudycelekli ). 
 Worker ports and IPv6 addresses are honored everywhere, and the uvx path can be set in settings ( @Ravencloned ). 
 
 
 Providers and streaming: 
 
 OpenCode Go session header ( @Cassian433 ). 
 Sturdier streamed replies, emoji never split when long output is trimmed, and Zstandard transcripts keep their text intact ( @rudycelekli ). 
 
 
 Server runtime: 
 
 Fresh installs no longer get 403 errors ( @DeryFerd ). 
 File edits reach the server, and CLAUDE_MEM_SKIP_TOOLS is honored in server mode ( @DeryFerd ). 
 Stuck jobs are reclaimed ( @escooterclinic ). 
 No stray local database ( @vinay121314 ). 
 Leaner prompts ( @rich-murphey ). 
 Postgres keeps literal __proto__ keys in stored JSON ( @rudycelekli ). 
 Stricter Redis settings ( @rudycelekli ). 
 
 
 Sync, Chroma and duplicates: 
 
 Prompts from other devices are linked ( @necatisozer ). 
 Turning Chroma off is fully honored ( @CCCLL ). 
 Fewer Chroma rewrites at startup ( @Montinou ). 
 Accent-aware duplicate detection ( @rudycelekli ) and a corrected similarity threshold ( @udsy19 ). 
 
 
 Viewer: 
 
 "Select all" in the Logs drawer works ( @DrDLyuan ). 
 The context preview opens on a project that has data ( @rudycelekli ). 
 
 
 
 Project 
 
 main is now the only branch. core-dev and community-edge are retired, so please open pull requests against main .