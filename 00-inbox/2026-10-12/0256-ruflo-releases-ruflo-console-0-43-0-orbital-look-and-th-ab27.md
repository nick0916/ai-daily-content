---
id: inbox_c9e01f53
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/ruflo-console-v0.43.0"
author: "ruvnet"
published_at: 2026-10-12T12:55:22+00:00
fetched_at: 2026-10-18T02:56:54.700719+00:00
content_hash: "ab27a64743c44f82b8279fbf6817a7b0c5f280d8468ee2dd085b905d95f62742"
lang: en
caption_quality: None
raw: true
topics: []
---

# ruflo-console 0.43.0: Orbital look and Theme Studio

ruflo-console 0.43.0: optional Orbital look and Theme Studio 
 Classic BBS stays the default. Orbital is opt-in; nothing changes until you pick it. 
 Changelog 
 
 feat: an optional Orbital look: black telemetry panels, square borders, a rotating globe, a scan sweep and a shaded RUFLO header that stays visible after boot (Main Menu, Theme Studio, Swarm), animated real boot checks, a perspective swarm preview. 
 feat: Theme Studio (Main Menu → Tools, Settings, or /ruflo themes ): pick Classic BBS, Terminal plain or Orbital; six bundled color presets; up to twelve named custom themes saved through host storage; a color picker with a 3:1 minimum contrast; motion layers and speed; fps 0 freezes the frame. 
 feat: a bundled generate-console-theme skill ( allowed-tools: Read ) returns data-only palette/motion JSON for Claude or Codex; import goes through a strict, 4096-character-bounded schema. 
 fix: Theme Studio has a boot-log line and a help guide and is reached by name; the wide Orbital header says RUFLO, not RUVNET. 
 chore: the globe reads a one-degree land mask built once (about a third less time per frame); scripts/bench-theme.mjs ; no Python in the repo (the SVG demo exporter is Node). 
 
 Validation 
 
 Console tests: 0 failing (main and this release both skip 29 files that need claude-code/testing ); 3193 pass (+77). Console smoke 20/20; manifest, mcp-prefix, skill-frontmatter, hook audits and claude plugin validate pass; CI 114 checks green. 
 Checked in the real Claude Code 2.1.289 (isolated config, directory marketplace, tmux, frames viewed): /ruflo , Orbital and Classic, Tools → Theme Studio, /ruflo themes , colour edit, contrast guard, save and reload across a full restart, "Use configured look", malformed/hostile JSON rejected with the theme unchanged, animation running (12/12 distinct frames) and stopped at fps 0, resizes 300→150 columns, clean model-facing console_state (no escapes, no theme JSON). 
 45 adversarial specs on import, stores and model-facing text found no defect. Classic BBS per-tick cost is unchanged from before. 
 
 Not verified 
 Windows and macOS terminals, other emulators (tmux 256-colour only), the desktop and VS Code surfaces, a real AI-generated theme round trip (Generate with Claude/Codex was not run), and some stray │ cells right of the pane after a shrink-resize in tmux (looks like host diff-render residue). The side-by-side editor layout needs a pane of 100+ columns (the host's default share is narrower; RUFLO_CONSOLE_COLUMNS widens it). 
 Install 
 Marketplace plugin, not npm: claude plugin marketplace update ruflo then claude plugin update ruflo-console@ruflo , and restart Claude Code. 
 PR #4079 . Orbital and Theme Studio by @ruvnet (with Codex); review, fixes, validation and optimization by RuFlo.