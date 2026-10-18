---
id: inbox_846944cd
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/v13.40.0"
author: "thedotmack"
published_at: 2026-10-16T12:25:04+00:00
fetched_at: 2026-10-18T02:56:55.887982+00:00
content_hash: "eaccc12996731e2958724bde3addce96079c3db902123a72986dfcc3be70d7e0"
lang: en
caption_quality: None
raw: true
topics: []
---

# v13.40.0

What's new 
 TeamBrain from the terminal 
 
 npx claude-mem teambrain join &lt;invite-link&gt; connects this install to a TeamBrain team using the same device-code sign-in as install . You approve the device in the browser, then choose which projects to share. Also: teambrain status , teambrain share , teambrain leave , teambrain start . ( #4815 ) 
 Members who join with a team seat keep their own local observer — joining never switches your observer provider. 
 When an install belongs to a team, SessionStart adds a short team brief : open collisions in this project, recent plans and decisions, who else is active, and items delegated to you. Agents also get read-only team_brief and team_search MCP tools. Installs that are not in a team see no change. 
 
 Work-state sync 
 
 The agent's work-state tracker ( work_state_write / work_state_read ) now syncs to the cloud as a work_state content kind, for accounts where the sync server enables it. Until then rows wait locally — they are never dropped. Devices that skipped work-state ops on older builds apply them once after upgrading. ( #4569 ) 
 
 Also new 
 
 The Claude observer can batch queued events (opt-in). ( #4793 ) 
 Viewer: the NOTES summary section has its own icon ( #4776 ); long prompts clamp behind a "Show more" disclosure ( #4765 ). 
 
 Fixes 
 
 Codex: bundle Zod so cached hooks load without node_modules ( #4771 ); reject a host root without its dependencies in the hook resolver ( #4766 ); finish teardown before removing the private runtime ( #4792 ). 
 Search: reject an unparseable dateStart / dateEnd with 400 INVALID_DATE ( #4786 ); validate limit / offset with 400 INVALID_PAGINATION ( #4787 ); make the implicit 90-day recency window configurable ( #4773 ). 
 Privacy: strip nested and overlapping memory tags ( #4761 ); opt-in generic credential patterns, with the redaction settings documented ( #4762 ). 
 Ingest: register an unknown project when hook payloads have no cwd ( #4774 ); apply CLAUDE_MEM_SKIP_BASH_PATTERNS to the PowerShell tool ( #4756 ). 
 Hooks: skip SessionEnd for sessions that are never tracked ( #4780 ); fix hook spool delivery to remote workers ( #4626 ). 
 Worker: spare a silent worker whose liveness heartbeat is fresh, for a bounded time ( #4794 ). 
 Projects: promote a merged-from project to a read key only for whole-project merges ( #4789 ). 
 Context files: keep CLAUDE.md/AGENTS.md symlinks when refreshing context ( #4784 ). 
 Exclusions: a trailing /** pattern also excludes the directory itself ( #4785 ). 
 Cursor: preserve your own hooks.json entries on install/uninstall ( #4783 ). 
 Logger: keep the day log open instead of re-opening it per line ( #4791 ). 
 Launcher: ad-hoc re-sign the compiled binary on macOS before the protocol probe ( #4781 ). 
 CLI: show help for install , update , uninstall and other action verbs instead of running them ( #4767 ). 
 DSH: keep every table's header when collapsing duplicate rows ( #4790 ). 
 Tree-sitter: verify the CLI loads, not just that it exists ( #4777 ). 
 Build: leave posthog-node's optional OpenTelemetry import unresolved ( #4795 ). 
 
 Upgrade notes 
 
 The local database schema moves to v67 on first open. Older builds refuse a database a newer build has opened (no downgrade), so update every install that shares ~/.claude-mem . 
 If work-state sync is enabled for your account, your existing work-state history uploads once. 
 Using claude-mem on more than one machine? Update all of them — builds older than v13.29.0 cannot skip sync content they don't recognize.