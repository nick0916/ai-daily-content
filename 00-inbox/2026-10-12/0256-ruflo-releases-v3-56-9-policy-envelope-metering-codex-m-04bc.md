---
id: inbox_1686b5d5
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.56.9"
author: "ruvnet"
published_at: 2026-10-12T21:14:45+00:00
fetched_at: 2026-10-18T02:56:54.697702+00:00
content_hash: "04bc3982d3cb90e5f96cc38643a9276605cce1fb443c2fa84252248c7bf0a6fd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.56.9 — policy envelope metering, Codex MCP backend retired, CLI parser fixes, ruflo-mods guards

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.9 (latest, alpha, v3alpha). The bundled leaves @claude-flow/security 3.0.5 and @claude-flow/codex 3.0.5 were published standalone first, and the CLI pins them, @claude-flow/shared 3.0.5 and @claude-flow/cli-core 3.7.2 exactly. Signed helpers changed ( hook-handler.cjs , re-signed in #4096 ). 
 Fixed 
 
 Policy envelope ( security 3.0.5): explicit envelope ceilings require metering, and unmetered worker ceilings stay opt-in ( #3503 , @rudycelekli ). 
 Codex MCP backend ( codex 3.0.5 and the ruflo wrapper bridge): the opt-in codex backend no longer launches @openai/codex mcp-server , which current Codex CLI dropped, and is retired without a startup stall ( #3522 , @rudycelekli ; reported in #3509 by @pacphi ). 
 CLI parser, retry, rate-limit, monitoring and config fixes : a reviewed batch ( #4107 , covering #4000 - #4017 , @rudycelekli and others). 
 analyze diff renders the analyze_diff result shape ( #4102 , fixes #4101 , @z4forzubair ). 
 shared 3.0.5 and cli-core 3.7.2: narrow-column truncation, rate-window retry times, structured network error codes ( #4014 , #4015 , #4018 , @rudycelekli ). 
 ruflo-mods guards ( #4096 , @proffesor-for-testing ): the root-delete guard no longer misses brace, nesting and fork-bomb forms, the screen .env check is fixed, and init -generated hooks carry the changes. 
 Console (marketplace plugin; its tui.mjs is bundled into the CLI): worktree removal runs no fsmonitor or hooks and keeps untracked files ( #4092 ), console_state reports an expired confirm card ( #4067 ), pictures draw as SVG on Claude Code Desktop ( #4112 ), all by @proffesor-for-testing ; the Skills page pins its skills CLI ( #4113 , @martinvlad ). 
 ruflo-cost-tracker logs Stop-hook telemetry write failures instead of discarding them ( #3227 , @nicholas-ruest ; marketplace plugin). 
 CI runs every v3 root-suite test file and no longer accepts a crashed run as a pass ( #4099 , @proffesor-for-testing ); not part of the package. 
 
 Thanks 
 @rudycelekli , @proffesor-for-testing , @z4forzubair , @nicholas-ruest , @martinvlad , @ronmikailov (whose reports shaped the 3.56.7 and 3.56.8 trains) and @pacphi .