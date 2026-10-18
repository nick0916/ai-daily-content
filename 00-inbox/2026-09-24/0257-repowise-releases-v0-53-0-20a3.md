---
id: inbox_170b3184
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.53.0"
author: "github-actions[bot]"
published_at: 2026-09-24T09:33:10+00:00
fetched_at: 2026-10-18T02:57:00.746198+00:00
content_hash: "20a39e0c414413e7510dc2bd2a38ab5fd7430b24b66f530768cdc474fe62e08e"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.53.0

What's Changed 
 
 docs: correct what 0.52.0 changed, and give documentation drift a page by @RaghavChamadiya in #2480 
 feat(perf): plans that claim only what they can back, and an over-fetch detector by @RaghavChamadiya in #2495 
 refactor(core): move the lead fold into core, add heritage kinds, compare change health without a checkout by @RaghavChamadiya in #2494 
 fix(security): detect vendor credential shapes and PEM keys, not just variable names by @Aman-goel-04 in #2223 
 refactor(workspace): one dialect base for every contract type, and topics that follow RabbitMQ bindings by @RaghavChamadiya in #2501 
 feat(workspace): open contracts in a drawer, with search, paging and a needs-attention list by @RaghavChamadiya in #2497 
 fix(ui): scroll only the tab row when ViewTabs reveals its active tab by @RaghavChamadiya in #2498 
 feat(workspace): open co-changing file pairs in a drawer, with search and cap reporting by @RaghavChamadiya in #2499 
 feat(workspace): replace the System Map inspector with a drawer, lenses and findings by @RaghavChamadiya in #2500 
 fix(security): mask secrets in every stored snippet, and clear rows stored raw by @RaghavChamadiya in #2496 
 fix(communities): never name a community after a third-party module by @RaghavChamadiya in #2502 
 feat(graph): bundle community links in the Files view, and make it the default by @RaghavChamadiya in #2503 
 feat(perf): promote plans on facts that settle their prerequisites by @RaghavChamadiya in #2504 
 refactor(php): one composer reader and framework-facts registry, with PHP references the graph used to miss by @RaghavChamadiya in #2505 
 refactor(attention): move the ranking fold into core over plain records by @RaghavChamadiya in #2506 
 perf(server): load repowise.server.schemas submodules on first access by @RaghavChamadiya in #2507 
 refactor(test-impact): split analyze_test_impact into a session read and a pure assemble_test_impact by @RaghavChamadiya in #2508 
 fix(mcp): report an unknown search_codebase mode instead of coercing it by @8rulerstar in #2392 
 refactor(decisions): read acceptance requirements from plain records in lifecycle by @RaghavChamadiya in #2510 
 refactor(search): move query-shape routing into a module with no database import by @RaghavChamadiya in #2511 
 feat(laravel): serve routes under their groups, link registrations, and read migrations as tables by @RaghavChamadiya in #2512 
 feat(perf): read session.get as a query, and prove fewer batch plans than before by @RaghavChamadiya in #2513 
 feat(perf): keep repetition with nothing to change out of the default queue by @RaghavChamadiya in #2514 
 fix(health): keep the test named for a file when a validation list is capped by @RaghavChamadiya in #2515 
 fix(ui): give the health map the expected actionability state by @RaghavChamadiya in #2520 
 refactor(core): move knowledge silo ranking and onboarding targets into core by @RaghavChamadiya in #2517 
 refactor(core): move owner, module health and reviewer rollups into core by @RaghavChamadiya in #2518 
 refactor(core): move the refactoring summary chips into core by @RaghavChamadiya in #2519 
 refactor(ui): read the drawer's actionability words from ACTIONABILITY_LABEL by @RaghavChamadiya in #2522 
 fix(perf): prove fewer batch plans, and stop reading a plugin registry as a query by @RaghavChamadiya in #2521 
 feat(workspace): read queues, pub/sub and socket events across Laravel and Node by @RaghavChamadiya in #2525 
 feat(stats): one-page stats report, scoped windows and new records by @RaghavChamadiya in #2526 
 feat(workspace): read NestJS routes, Node HTTP clients and Node ORM tables by @RaghavChamadiya in #2527 
 feat(perf): flag a lazily loaded relationship read once per row in a loop by @RaghavChamadiya in #2528 
 refactor(workspace): serve workspace reads from importable functions by @RaghavChamadiya in #2530 
 feat(workspace): read Angular HttpClient calls and Angular app entry points by @RaghavChamadiya in #2531 
 fix(test-impact): report a failed head-commit read as degraded instead of absent by @Aman-goel-04 in #2529 
 fix(providers): make opencode subprocess concurrency configurable via shared resolver by @Aman-goel-04 in #2485 
 fix(mcp): keep pathless symbol rows out of get_answer's homonym union by @8rulerstar in #2391 
 fix(cli): honor REPOWISE_MODEL environment variable in provider resolution by @Tyagiquamar in #2276 
 fix(rust): inherit impl block visibility from target type/trait declaration ( #2389 ) by @rishu685 in #2427 
 fix(health): count Pascal for-in loops, add a performance dialect by @Laex in #2233 
 Derive LiteLLM reasoning capabilities from local metadata by @Selene29 in #2240 
 fix(cli): clear distill.commands.enabled and remove AGENTS.md on hook rewrite uninstall ( #2471 ) by @rishu685 in #2491 
 fix(claude): remove distill allow rules on uninstall and check in leftover reason ( #2470 ) by @rishu685 in #2483 
 release: v0.53.0 — Laravel, NestJS, Node and Angular contracts, and performance plans that claim only what they prove by @RaghavChamadiya in #2533 
 
 New Contributors 
 
 @8rulerstar made their first contribution in #2392 
 @Tyagiquamar made their first contribution in #2276 
 
 Full Changelog : v0.52.0...v0.53.0