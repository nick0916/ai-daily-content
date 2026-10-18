---
id: inbox_1cc2519b
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.52.0"
author: "github-actions[bot]"
published_at: 2026-09-20T12:31:37+00:00
fetched_at: 2026-10-18T02:57:00.747453+00:00
content_hash: "b297fa54ee4f3195bd70e0a2f0749001c84369344e42bb5885fef003407e2330"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.52.0

What's Changed 
 
 fix(mcp): keep the projection a caller asked for ahead of the ones they did not by @RaghavChamadiya in #2270 
 feat(mcp): report timing_ms for every tool, not just the ones that thread it by @RaghavChamadiya in #2271 
 perf(core): parse the index scope once per index state, not once per call by @RaghavChamadiya in #2272 
 feat(analysis): compose one change review over the existing primitives by @RaghavChamadiya in #2273 
 fix(change-risk): stop an unreadable fix record from reading as a clean one by @RaghavChamadiya in #2274 
 test(cli): pin what the risk command puts on stdout by @RaghavChamadiya in #2277 
 fix(decisions): require a stated reason before a record can be accepted by @RaghavChamadiya in #2279 
 docs(agent): how to review a change from Python by @RaghavChamadiya in #2281 
 fix(why): stop claiming a ruling the store does not hold by @RaghavChamadiya in #2280 
 fix(mcp): stop a path question from shedding the answer it asked for by @RaghavChamadiya in #2282 
 feat(mcp): name how a session ended instead of leaving it to look like a crash by @RaghavChamadiya in #2283 
 perf(mcp): serve a digest of the index scope, not the whole thing, on every call by @RaghavChamadiya in #2284 
 fix(mcp): give every requested hop a share of the callee budget by @RaghavChamadiya in #2285 
 feat(decisions): stop mining transcripts unless asked by @RaghavChamadiya in #2286 
 test(mcp): pin that an exact symbol name beats a crowd of fuzzy neighbours by @RaghavChamadiya in #2287 
 feat(doc-drift): check what documents claim about the tree by @RaghavChamadiya in #2290 
 test(why): pin that decisions dropped by the search cap stay recoverable by @RaghavChamadiya in #2291 
 fix(health): stop an unresolved scope from being answered with the whole repo by @RaghavChamadiya in #2292 
 feat(doc-drift): keep documentation findings current on every update by @RaghavChamadiya in #2307 
 fix(decisions): dedup paraphrases at the pass that creates the record by @RaghavChamadiya in #2310 
 test(mcp): pin the wire representations every tool actually serves by @RaghavChamadiya in #2311 
 fix(csharp): bind an extension-method call to the type it extends by @RaghavChamadiya in #2312 
 feat(doc-drift): surface documentation drift in the CLI and get_health by @RaghavChamadiya in #2313 
 fix(chat): stop suggesting questions no tool can answer by @RaghavChamadiya in #2315 
 feat(decisions): fold stored duplicate candidates in one sweep by @RaghavChamadiya in #2314 
 feat(health): measure test mock saturation without moving any score by @RaghavChamadiya in #2317 
 fix(mcp): key get_context's used_by on the symbol, not on its file by @RaghavChamadiya in #2329 
 fix(risk): stop answering an unresolved target with a confident zero by @RaghavChamadiya in #2321 
 feat(why): name the decision lanes the health dashboard only counted by @RaghavChamadiya in #2322 
 feat(decisions): fold record completeness into decision confidence by @RaghavChamadiya in #2328 
 feat(decisions): fill last_code_change from the dates staleness already reads by @RaghavChamadiya in #2357 
 feat(health): measure mock saturation on TypeScript, and refuse Java by @RaghavChamadiya in #2358 
 feat(doc-drift): answer which documents name a file by @RaghavChamadiya in #2356 
 fix(java): stop a bare @immutable fabricating a generated class by @RaghavChamadiya in #2361 
 Fix MCP tool toggles for workspace repositories by @Selene29 in #2241 
 Fix repository paths for server-side CLI providers by @Selene29 in #2242 
 fix(costs): price deepseek/kimi instead of $0 in estimator and live tracker by @Ayush7614 in #1790 
 fix(server): make CORS browser-compliant and configurable via env by @Ayush7614 in #1793 
 fix(security): store provider_config 0600 and redact keys in validate response by @Ayush7614 in #1798 
 fix(mcp): name the capability, not one host's tool names, in no-index guidance by @sloemo01 in #2326 
 fix(swift): stop a qualified extension naming its qualifier as a parent by @sloemo01 in #2318 
 fix(graph): pair Objective-C .h and .m header/implementation files by @sloemo01 in #2323 
 fix(godot): resolve uid:// references to scripts through their .uid sidecars by @sloemo01 in #2336 
 fix(objectivec): blank call-shaped availability macros trailing a declaration by @sloemo01 in #2330 
 fix(ingestion): capture C# null-conditional call sites by @sloemo01 in #2324 
 fix(claude_cli): count the whole prompt in token totals and record the run's cost by @sloemo01 in #2337 
 fix(delete): delete a repository the configured database knows about by @sloemo01 in #2338 
 fix(server): zero total_pages when a phase reports no total by @Aman-goel-04 in #2308 
 fix(ui): stop prerendering the root layout's repo list ( #2260 ) by @punk-dev-robot in #2261 
 fix(mcp): make local-endpoint budgets configurable by @NullSense in #1856 
 feat(embedding): declare a model's width without sending dimensions by @NullSense in #1857 
 fix(rust): parent a trait's defaulted methods to the trait by @RaghavChamadiya in #2362 
 feat(doc-drift): put documentation drift on the dashboard by @RaghavChamadiya in #2370 
 fix(health): exclude Rust inline test code from perf findings by @NullSense in #1855 
 docs(contributing): make a claim binding and correct the stale setup steps by @RaghavChamadiya in #2377 
 fix(rust): give a trait's items the visibility the trait declares by @RaghavChamadiya in #2376 
 fix(health): build the perf test's ranker through the current API by @RaghavChamadiya in #2383 
 feat(doc-drift): open one finding's evidence and hand it to an agent by @RaghavChamadiya in #2378 
 feat(health): count assertions with a per-language vocabulary by @RaghavChamadiya in #2371 
 feat(rust): capture bodiless fn declarations as symbols by @RaghavChamadiya in #2382 
 feat(savings): add canonical event accounting by @RaghavChamadiya in #2248 
 fix(sessions): scope Codex transcripts to the repo that owns them by @RaghavChamadiya in #2387 
 docs(dead-code): give the Rust unused_internal skip its real reason by @RaghavChamadiya in #2390 
 feat(health): flag a test case that checks nothing by @RaghavChamadiya in #2393 
 refactor(agents): define each agent once, and stop savings enumerating them by @RaghavChamadiya in #2394 
 fix: capture field_declarations types to omit rust dead code fps by @crizah in #1568 
 fix(decisions): bind a session-mined decision to code the repo actually has by @RaghavChamadiya in #2395 
 fix(health): read a .tsx file with the JSX grammar by @RaghavChamadiya in #2398 
 feat(savings): record one canonical event per logical interaction by @RaghavChamadiya in #2401 
 feat(health): let a called function's assertions reach its caller by @RaghavChamadiya in #2399 
 feat(decisions): tell a working agreement apart from a decision about the code by @RaghavChamadiya in #2405 
 fix(health): stop dropping a file's same-named functions before a marker sees them by @RaghavChamadiya in #2408 
 fix(savings): report the same numbers from the API, the overview and the CLI by @RaghavChamadiya in #2413 
 fix(health): judge a finding by its own deduction, not its share of a capped category by @RaghavChamadiya in #2411 
 feat(decisions): deliver a working agreement to the agent, and let a person type one by @RaghavChamadiya in #2410 
 fix(rust): bind a scoped call to its own type, not the file's last by @RaghavChamadiya in #2409 
 fix(rust): carry the rest of the path through a crate-root re-export by @RaghavChamadiya in #2412 
 fix(heritage): anchor an inheritance edge to the child's real symbol id by @RaghavChamadiya in #2414 
 feat(decisions): tell an agent a candidate from a rule it can follow by @RaghavChamadiya in #2420 
 fix(rust): stop reading a trait bound as inheritance by @RaghavChamadiya in #2415 
 feat(health): resolve a test's oracle across a file boundary by @RaghavChamadiya in #2419 
 fix(decisions): store staged decision paths the index can resolve by @RaghavChamadiya in #2421 
 feat(decisions): flag a bundled claim on every capture path, not one lane by @RaghavChamadiya in #2422 
 fix(rust): refuse a std-library name on the import_merged tier by @RaghavChamadiya in #2423 
 fix(health): narrow assertion_free_test to tests that really check nothing by @RaghavChamadiya in #2424 
 feat(decisions): key a decision on its evidence rather than on its title by @RaghavChamadiya in #2425 
 feat(decisions): promote a candidate that states a reason, not one seen twice by @RaghavChamadiya in #2426 
 fix(health): let a surface that ranks nothing see a zero-impact finding by @RaghavChamadiya in #2430 
 fix(tests): vary the decision body so two doctor fixtures are two records by @RaghavChamadiya in #2431 
 feat(savings): rebuild the costs page as an evidence-led scan surface by @RaghavChamadiya in #2432 
 feat(overview): merge every detector into one attention list by @RaghavChamadiya in #2429 
 feat(decisions): a commit's file list stops answering per-file questions by @RaghavChamadiya in #2434 
 fix(health): count a test's oracle wherever it sits in a with header by @RaghavChamadiya in #2436 
 fix(health): measure co-change breadth instead of counting a capped list by @RaghavChamadiya in #2437 
 fix(decisions): lower the governing-scope cutoff from ten files to five by @RaghavChamadiya in #2439 
 fix(health): rank the remaining history gates against the repository by @RaghavChamadiya in #2438 
 feat(savings): recover the savings agents were shown but nobody banked by @RaghavChamadiya in #2440 
 fix(risk): publish a churn rank beside the raw churn sum on direct risks by @RaghavChamadiya in #2443 
 test(savings): stop the test suite banking savings in the real repository by @RaghavChamadiya in #2442 
 feat(decisions): ask the miner which files a commit's decision is about by @RaghavChamadiya in #2441 
 fix(decisions): stop the scope repair demoting what a person accepted by @RaghavChamadiya in #2445 
 fix(update): stop a failed HEAD read stranding a store's sync pointer by @RaghavChamadiya in #2446 
 fix(decisions): stop a starved token budget silently losing whole batches by @RaghavChamadiya in #2447 
 fix(decisions): stop one wordy candidate silencing the whole lane by @RaghavChamadiya in #2450 
 feat(decisions): let a measured capture tier deliver without an acceptance by @RaghavChamadiya in #2451 
 feat(change-risk): report what the change wrote, not what it weighs by @RaghavChamadiya in #2452 
 fix(distill): run a wrapped command in the shell it was written for by @RaghavChamadiya in #2448 
 feat(commits): lead the commit sheet with where the change lands by @RaghavChamadiya in #2453 
 feat(commits): filter the repository, not the loaded page by @RaghavChamadiya in #2455 
 perf(mcp): stop sending the same fact twice in a tool response by @RaghavChamadiya in #2456 
 feat(decisions): record what signed an acceptance, not only who by @RaghavChamadiya in #2457 
 feat(generation): say when a standing decision was not signed by a person by @RaghavChamadiya in #2458 
 feat(commits): store which files each commit touched by @RaghavChamadiya in #2459 
 fix(security): mask secret values in security finding snippets ( #2119 ) by @akshatmalik-bruh in #2375 
 fix(ingestion): resolve a nested sub-package from its own manifest by @Aman-goel-04 in #2402 
 fix(rust): widen type_use captures to wrapper shapes by @Aman-goel-04 in #2386 
 fix(generation): stop a formatter comment from prescribing ruff format by @Aman-goel-04 in #2444 
 fix(godot): resolve scene connections to C# script methods by @Aman-goel-04 in #2316 
 fix(dead-code): treat Rust impl blocks as uncallable and non-importable ( #2388 ) by @rishu685 in #2418 
 fix(ingestion): mint reference edges for Go functions in composite literals ( #2351 ) by @rishu685 in #2363 
 fix(mcp): remove dead context_hint and clean up get_context ( #2348 ) by @rishu685 in #2369 
 fix(workspace): allow removing missing workspace repos from UI ( #2234 ) by @rishu685 in #2253 
 fix(ingestion): index TypeScript class fields holdi

[... truncated for safety ...]