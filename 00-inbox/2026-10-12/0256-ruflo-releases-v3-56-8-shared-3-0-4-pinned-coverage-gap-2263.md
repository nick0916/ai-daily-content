---
id: inbox_fb6b0a3d
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.56.8"
author: "ruvnet"
published_at: 2026-10-12T17:40:51+00:00
fetched_at: 2026-10-18T02:56:54.698938+00:00
content_hash: "2263ea773c68a898026f4a909e757dbd0e19a9cb73ea1d82972f244725790590"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.56.8 — shared 3.0.4 pinned, coverage-gaps fixes, TUI page bar

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.8 (latest, alpha, v3alpha). The CLI now pins @claude-flow/shared 3.0.4 (3.56.7 still pinned 3.0.3). No other published package changed since 3.56.7; signed helpers did not change. 
 Fixed 
 
 @claude-flow/shared 3.0.4 : the RVF event log repairs an incomplete or damaged tail before appending ( #4031 , @rudycelekli ). A clean install can import . , ./core and ./mcp because zod and express are now declared, and the tarball no longer ships compiled tests ( #4089 , #4091 , @proffesor-for-testing ). The fresh-consumer finding behind this came from @martinvlad , and scripts/smoke-shared-fresh-consumer.mjs now covers it. 
 hooks coverage-gaps : files with no executable lines are no longer reported as 0%, overall coverage is line-weighted, the command reads coverage-final.json , and report size is capped ( #4082 - #4084 reported by @ronmikailov ; #4097 ). Plugin workflow contracts for ruflo-testgen and ruflo-sparc were corrected in the same change ( #4085 - #4088 ; marketplace plugins, not npm). 
 ruflo tui : the page bar marks the AI page (6 AI) when started with --view ai , and the help text says pages 1-6 ( #4105 , #4106 ). The policy-trust path is never resolved relative to the working directory ( #4106 ). 
 The README and docs now cover ruflo tui with the animated walkthrough ( #4103 ). 
 
 Thanks 
 @rudycelekli , @proffesor-for-testing , @martinvlad , @ronmikailov and @Devesh-Maheshwari for the reports and fixes that shaped 3.56.6 through 3.56.8.