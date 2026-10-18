---
id: inbox_9f61f146
date: 2026-09-30
source_ref: "[[00-inbox/2026-09-30/0257-repowise-releases-v0-54-0-c128]]"
title: "v0.54.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.54.0
source: repowise-releases
published_at: 2026-09-30T07:29:03+00:00
fetched_at: 2026-10-18T03:23:08.883684+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.54.0 發布（內容在原文中被截斷，以下僅依可見部分整理）。此版本絕大多數變更是大規模重構：將 server 端的 get_health、get_why、execute_job、repos router、tool_overview 等長函式拆解成小模組，core 端也拆分 decision miners、ASTParser、KG tour、CallResolver 等。功能面新增三個 CI gate：patch coverage（#2630）、documentation drift（#2631，會建議替換內容）、security（#2635，針對變更新增的 findings），並提供一個 GitHub Action、GitLab template 與一份共用指南（#2641），另有 coverage 歷史與趨勢（#2642）。修正項目包含 git 歷史跨 rename 保留（#2569）、history window 以 indexed commit 而非 wall clock 計算（#2568）、health 分數顯示向下取整避免進位到下一個 band（#2587）、hidden_coupling 不再扣分而改為 advisory（#2596）。對使用 Repowise 做程式碼健康度與 CI 把關的團隊較有實務意義。"
key_points:
  - "新增三個 CI gate：patch coverage（#2630）、doc-drift（#2631）、security findings（#2635），並提供單一 GitHub Action 與 GitLab template（#2641）"
  - "health 評分調整：hidden_coupling 改為 advisory 不再扣分（#2596），顯示分數改為向下取整（#2587）"
  - "git 歷史修正：跨 rename 保留檔案歷史（#2569），history window 以 indexed commit 計算（#2568）"
tags: [repowise, ci-gate, patch-coverage, doc-drift, refactoring]
topics: [agents.coding_agents, engineering.evals]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.54.0

Repowise v0.54.0 發布（內容在原文中被截斷，以下僅依可見部分整理）。此版本絕大多數變更是大規模重構：將 server 端的 get_health、get_why、execute_job、repos router、tool_overview 等長函式拆解成小模組，core 端也拆分 decision miners、ASTParser、KG tour、CallResolver 等。功能面新增三個 CI gate：patch coverage（#2630）、documentation drift（#2631，會建議替換內容）、security（#2635，針對變更新增的 findings），並提供一個 GitHub Action、GitLab template 與一份共用指南（#2641），另有 coverage 歷史與趨勢（#2642）。修正項目包含 git 歷史跨 rename 保留（#2569）、history window 以 indexed commit 而非 wall clock 計算（#2568）、health 分數顯示向下取整避免進位到下一個 band（#2587）、hidden_coupling 不再扣分而改為 advisory（#2596）。對使用 Repowise 做程式碼健康度與 CI 把關的團隊較有實務意義。

### 重點
- 新增三個 CI gate：patch coverage（#2630）、doc-drift（#2631）、security findings（#2635），並提供單一 GitHub Action 與 GitLab template（#2641）
- health 評分調整：hidden_coupling 改為 advisory 不再扣分（#2596），顯示分數改為向下取整（#2587）
- git 歷史修正：跨 rename 保留檔案歷史（#2569），history window 以 indexed commit 計算（#2568）

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.54.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's Changed 
 
 refactor(server): decompose get_health into a thin dispatcher by @RaghavChamadiya in #2546 
 refactor(server): split get_why into mode and layer modules by @RaghavChamadiya in #2547 
 refactor(server): split tool_answer/symbols.py and give the string scanner one handler per state by @RaghavChamadiya in #2548 
 refactor(server): decompose execute_job and split job_executor along its section seams by @RaghavChamadiya in #2549 
 test(server): pin the /api/repos branches the feature tests leave uncovered by @RaghavChamadiya in #2550 
 refactor(server): split the repos router's summary, listing, pricing and generate helpers out of its long handlers by @RaghavChamadiya in #2551 
 fix(core): close the omission store's connection when opening it fails by @RaghavChamadiya in #2555 
 refactor(core): decompose the decision miners and share their batching by @RaghavChamadiya in #2559 
 refactor(core): share OpenAI-compatible provider plumbing by @RaghavChamadiya in #2557 
 refactor(core): split crud/decisions.py by concern by @RaghavChamadiya in #2558 
 test(server): pin the degraded and edge paths of get_context enrichment, get_overview, get_change_risk and get_symbol by @RaghavChamadiya in #2556 
 fix(server): treat a missing repository as no index in change-risk health references by @RaghavChamadiya in #2553 
 refactor(core): move the KG tour out of kg_curation.py by @RaghavChamadiya in #2560 
 refactor(core): decompose the dead-code symbol and package passes by @RaghavChamadiya in #2561 
 refactor(core): decompose ASTParser symbol, import and call extraction by @RaghavChamadiya in #2562 
 refactor(core): flatten the Android manifest and .NET hint extractors by @RaghavChamadiya in #2563 
 fix(server): check for a repo path before building get_symbol's exclusion spec by @RaghavChamadiya in #2554 
 fix(health): a file with no code finding loses at most one point to git history by @RaghavChamadiya in #2566 
 fix(git): keep a file's history across renames by @RaghavChamadiya in #2569 
 fix(refactoring): attach only the findings a step's target answers by @RaghavChamadiya in #2571 
 fix(refactoring): stop move_method targeting result types and base classes by @RaghavChamadiya in #2572 
 fix(coupling): count a chain through a re-export barrel as a dependency by @RaghavChamadiya in #2573 
 fix(health): pair a file with the tests that import it by @RaghavChamadiya in #2574 
 fix(refactoring): credit extract_method only with the impact its span recovers by @RaghavChamadiya in #2570 
 fix(update): finish --full when a few pages fail, and stop truncating Ollama prompts by @RaghavChamadiya in #2564 
 refactor(server): split the HTTP lifespan into named startup and shutdown steps by @RaghavChamadiya in #2552 
 fix(git): measure history windows from the indexed commit, not the wall clock by @RaghavChamadiya in #2568 
 docs(server): shorten comments in the get_answer tool package by @RaghavChamadiya in #2576 
 docs(core): shorten comments in the receiver-type scanner by @RaghavChamadiya in #2577 
 docs(server): shorten comments in get_context target resolution by @RaghavChamadiya in #2579 
 docs(core): shorten comments in the dead-code constants by @RaghavChamadiya in #2578 
 docs(core): shorten comments in the session decision miner by @RaghavChamadiya in #2580 
 refactor(server): move chat prompt, history and tool summaries out of the chat router by @RaghavChamadiya in #2575 
 refactor(cli): move decision id resolution and batch runs into decision_batch by @RaghavChamadiya in #2581 
 refactor(core): break up FileTraverser's file filter and the console-script reader by @RaghavChamadiya in #2582 
 refactor(core): move per-language parser helpers into ingestion/lang_helpers by @RaghavChamadiya in #2584 
 refactor(ui): split ai-prompt-builder into one module per prompt kind by @RaghavChamadiya in #2585 
 fix(decisions): keep conventional ADR dirs ahead of loose name matches at the cap by @RaghavChamadiya in #2586 
 fix(health): floor displayed scores so the figure never rounds into the next band by @RaghavChamadiya in #2587 
 fix(why): match archaeology cross-references on whole tokens by @RaghavChamadiya in #2588 
 refactor(core): move decision records, answer parsing, staleness and commit helpers out of the extractor by @RaghavChamadiya in #2589 
 refactor(core): move C/C++ macro state tracking into cpp_macro_facts by @RaghavChamadiya in #2590 
 refactor(core): decompose the KG tour into named stages by @RaghavChamadiya in #2593 
 refactor(core): move KG module derivation and validation out of kg_curation.py by @RaghavChamadiya in #2592 
 refactor(server): split tool_overview.py into a package, moving code verbatim by @RaghavChamadiya in #2595 
 refactor(core): move call resolver language strategies and receiver typing into mixins by @RaghavChamadiya in #2594 
 fix(health): stop hidden_coupling deducting from the score, keep it as advisory by @RaghavChamadiya in #2596 
 refactor(core): make tech stack and build command detection table-driven by @RaghavChamadiya in #2597 
 refactor(server): split get_risk into graph loading, hotspot, evidence and directive steps by @RaghavChamadiya in #2598 
 refactor(core): move the TS/JS perf marker hooks into their own module by @RaghavChamadiya in #2599 
 refactor(server): split overlay ingestion and share artifact reads in CrossRepoEnricher by @RaghavChamadiya in #2600 
 refactor(server): decompose the decisions router's long handlers by @RaghavChamadiya in #2602 
 refactor(core): decompose the split_file detector into single-purpose helpers by @RaghavChamadiya in #2603 
 refactor(server): split symbol resolution and flow tracing out of the graph intelligence routes by @RaghavChamadiya in #2604 
 fix(decisions): read significant-commit metadata the same way in both commit miners by @RaghavChamadiya in #2605 
 refactor(core): decompose the shared commit-index walks into small steps by @RaghavChamadiya in #2606 
 refactor(core): split per-file history indexing into named steps by @RaghavChamadiya in #2607 
 fix(editor-files): keep a malformed manifest from crashing the tech stack scan by @RaghavChamadiya in #2608 
 refactor(ingestion): drop an unused per-file strategy map from CallResolver by @RaghavChamadiya in #2609 
 fix(mcp): describe the ownership block get_overview actually returns by @RaghavChamadiya in #2610 
 fix(ui): put text-xs and text-sm on the type ladder (12px and 15px) by @RaghavChamadiya in #2619 
 docs(security): hosted platform calls the LLM with its own key only by @RaghavChamadiya in #2617 
 fix(health): keep history markers through the update's full re-score by @RaghavChamadiya in #2614 
 fix(generate): account for every planned page and print the actual cost by @RaghavChamadiya in #2615 
 fix(decisions): stop the id migration copying a record onto an occupied id by @RaghavChamadiya in #2613 
 fix(update): split the cascade-budget warning into model and structural pages by @RaghavChamadiya in #2616 
 feat(coverage): gate a change on its patch coverage in CI by @RaghavChamadiya in #2630 
 feat(doc-drift): suggest replacements and gate documentation drift in CI by @RaghavChamadiya in #2631 
 fix(agent-targets): stop re-rendering .mcp.json when the merge refuses by @sloemo01 in #1836 
 feat(coverage): patch coverage on the agent, API and local surfaces by @RaghavChamadiya in #2634 
 feat(security): gate a change on the findings it adds in CI by @RaghavChamadiya in #2635 
 feat(coverage): record each ingest and report its freshness and path matches by @RaghavChamadiya in #2636 
 fix(coverage): match report paths by directory, report location and source roots by @RaghavChamadiya in #2637 
 feat(ci): one GitHub Action, a GitLab template and one guide for the three CI gates by @RaghavChamadiya in #2641 
 feat(coverage): keep a coverage history and show its trend by @RaghavChamadiya in #2642 
 feat(doc-drift): scope the CI gate to the drift a change is answerable for by @RaghavChamadiya in #2640 
 feat(vscode): show documentation drift in the Problems panel for markdown by @RaghavChamadiya in #2648 
 feat(doc-drift): record drift in health history and mark findings new since the last update by @RaghavChamadiya in #2646 
 feat(doc-drift): group findings by document and show which documents name a file by @RaghavChamadiya in #2647 
 feat(ci): write doc-drift and security findings as a GitLab Code Quality report by @RaghavChamadiya in #2643 
 feat(coverage): report globs, per-report prefixes, ignore globs and a small-change tolerance for the patch gate by @RaghavChamadiya in #2644 
 feat(coverage): path-scoped coverage gates, with suggestions from owners, layout and the graph by @RaghavChamadiya in #2649 
 feat(risk): gate a change on its risk percentile and weight patch coverage by risk by @RaghavChamadiya in #2645 
 feat(coverage): name the test to extend for each uncovered change, and keep an agent's coverage current by @RaghavChamadiya in #2650 
 feat(actions): lead the Overview with "Do next", built from stored evidence by @RaghavChamadiya in #2651 
 fix(security-scan): ignore call kinds in comments, strings and prose by @Aman-goel-04 in #2618 
 fix(security-scan): report credentials, not examples of them by @RaghavChamadiya in #2660 
 fix(ui): handle communities outside top 20 in GraphNarrowingSelect ( #2626 ) by @rishu685 in #2656 
 docs(graph): sync hand-graded benchmark figures with BENCHMARKS.md ( #2352 ) by @rishu685 in #2628 
 docs(dead-code): correct dynamic-import language coverage in DEAD_CODE.md and dynamic_markers.py ( #2354 ) by @rishu685 in #2629 
 fix(sessions): map codex function_call events to the assistant kind by @Aman-goel-04 in #2652 
 fix(ingestion): use the importable module for Python qualified names by @Aman-goel-04 in #2612 
 fix(ui): merge RepoAvatar className with cn() so callers can override display by @kokokoXUY in #2583 
 [Docs] Fix stale FILE_CODE_EDGE_TYPES reference by @Ava-91 in #2536 
 docs(dead-code): list all unused export edge types by @spark-328 in #2477 
 fix(ui): keep commit filters visible on empty results by @ayush2115 in #2487 
 Fix #2379 : Classify .env dotfiles as config paths by @pamod-madubashana in #2381 
 fix: account for Anthropic cached input tokens by @Hitesh-XS in #2433 
 fix: report non-executable post-commit hooks by @spark-328 in #2476 
 fix(hook): filter workspace targets and report failures by @spark-328 in #2478 
 fix(health): derive coverage-gap uncovered lines from the percentage by @JikSau-D in #2259 
 fix: classify dotfiles named after a config extension in file_category by @zhongxiao-chang in #2516 
 fix(lint): sort imports and drop extra parentheses in the language-support docs test by @RaghavChamadiya in #2666 
 feat(doc-drift): flag renamed or deleted code symbols named in docs, and suggest the fix on every surface by @RaghavChamadiya in #2661 
 feat(coverage): compare project coverage with the base and list coverage that moved outside the change by @RaghavChamadiya in #2659 
 feat(security): inline suppression marker, custom patterns and a pre-commit mode by @RaghavChamadiya in #2657 
 fix(coverage): use the renamed diff arguments when reading a change for the project delta by @RaghavChamadiya in #2667 
 feat(coverage): report branches on changed lines beside patch coverage, with partly taken lines and a branch gate by @RaghavChamadiya in #2664 
 feat(coverage): re-ingest after failing test runs, accept globs in coverage add, and show the trend in get_health by @RaghavChamadiya in #2658 
 fix(health): keep get_health's targeted analysis meta inside its session by @RaghavChamadiya in #2670 
 fix(dead-code): stop flagging internals used in their own file, files named by path, and receiver-registered functions by @swati510 in #2673 
 fix(ingestion): resolve Python imports by full dotted path, never by stem by @swati510 in #2674 
 feat(decisions): retire decisions whose commits were reverted by @swati510 in #2675 
 fix(graph): no file self-loops in the graph 

[... truncated for safety ...]

</details>