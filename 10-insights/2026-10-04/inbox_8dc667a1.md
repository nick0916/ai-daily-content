---
id: inbox_8dc667a1
date: 2026-10-04
source_ref: "[[00-inbox/2026-10-04/0257-repowise-releases-v0-55-0-0dcc]]"
title: "v0.55.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.55.0
source: repowise-releases
published_at: 2026-10-04T04:40:49+00:00
fetched_at: 2026-10-18T03:22:43.605304+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.55.0 為大型累積更新，重點在多語言符號解析的正確性與 Code Health 的「Fix first」佇列。解析方面：Java、C#、C++ 的 overload 各自擁有獨立 symbol（#2811、#2829），並修正 Go、Rust、Python（super() 依 MRO 解析）、TypeScript（物件字面值方法成為獨立 symbol）、C# partial class 等的型別與呼叫解析。Health 方面：新增橫跨 defect、maintainability、performance 的單一 Fix first 佇列（#2821），並依「每個要修改的位置一個 opportunity、依價值排序」重組 performance 結果（#2817）；Code Health 頁面改以 Fix first 為首（#2831）；重新索引後保留 finding triage（#2819）。MCP 與效能方面：get_context 在多個 target 間共用 budget（#2727）、dead-code 改讀已儲存的 findings 而非重新解析（#2769）、get_risk 只讀取目標的圖譜鄰域（#2763）；dead-code 也能連結 serverless、SAM、Terraform 設定中的 Lambda handler（#2834）。另新增 `present` 功能以短篇故事方式描述 repo（#2734）。原文在中途被截斷。"
key_points:
  - "Java、C#、C++ 的 overload 各自擁有獨立 symbol（#2811、#2829），Python super() 改依 MRO 解析（#2773）"
  - "新增跨 defect／maintainability／performance 的單一 Fix first 佇列（#2821），performance 改為每個修改位置一個 opportunity 並依價值排序（#2817）"
  - "dead-code 改讀已儲存 findings 而非重新 parse repo（#2769）；get_context 在多 target 間共用 budget（#2727）"
tags: [repowise, code-graph, code-health, fix-first, mcp]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.55.0

Repowise v0.55.0 為大型累積更新，重點在多語言符號解析的正確性與 Code Health 的「Fix first」佇列。解析方面：Java、C#、C++ 的 overload 各自擁有獨立 symbol（#2811、#2829），並修正 Go、Rust、Python（super() 依 MRO 解析）、TypeScript（物件字面值方法成為獨立 symbol）、C# partial class 等的型別與呼叫解析。Health 方面：新增橫跨 defect、maintainability、performance 的單一 Fix first 佇列（#2821），並依「每個要修改的位置一個 opportunity、依價值排序」重組 performance 結果（#2817）；Code Health 頁面改以 Fix first 為首（#2831）；重新索引後保留 finding triage（#2819）。MCP 與效能方面：get_context 在多個 target 間共用 budget（#2727）、dead-code 改讀已儲存的 findings 而非重新解析（#2769）、get_risk 只讀取目標的圖譜鄰域（#2763）；dead-code 也能連結 serverless、SAM、Terraform 設定中的 Lambda handler（#2834）。另新增 `present` 功能以短篇故事方式描述 repo（#2734）。原文在中途被截斷。

### 重點
- Java、C#、C++ 的 overload 各自擁有獨立 symbol（#2811、#2829），Python super() 改依 MRO 解析（#2773）
- 新增跨 defect／maintainability／performance 的單一 Fix first 佇列（#2821），performance 改為每個修改位置一個 opportunity 並依價值排序（#2817）
- dead-code 改讀已儲存 findings 而非重新 parse repo（#2769）；get_context 在多 target 間共用 budget（#2727）

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.55.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's Changed 
 
 fix(generation): keep knowledge-graph layer names unique by @RaghavChamadiya in #2725 
 fix(mcp): stop listing the test layer as an architecture layer by @RaghavChamadiya in #2726 
 fix(mcp): share get_context's budget across targets instead of dropping one by @RaghavChamadiya in #2727 
 fix(mcp): return the repo='all' error dict from get_health and the finding tools by @RaghavChamadiya in #2728 
 fix(ui): read the tiered get_dead_code shape in the chat card by @RaghavChamadiya in #2729 
 feat(ui): show the owner's line share and the merge commit count by @RaghavChamadiya in #2730 
 feat(ui): a steps-unavailable state in the opportunity drawer by @RaghavChamadiya in #2732 
 feat(ui): name the worst test file and mark unverified findings by @RaghavChamadiya in #2733 
 feat(present): tell the repository as a short story by @RaghavChamadiya in #2734 
 docs: correct stale MCP tool reference entries and document savings sync by @RaghavChamadiya in #2724 
 perf(mcp): build get_answer's graph projections once per index state by @RaghavChamadiya in #2735 
 fix(mcp): read a typed identifier as one name in get_answer retrieval by @RaghavChamadiya in #2736 
 fix(mcp): answer 'what happens when' questions from the entry's call order by @RaghavChamadiya in #2737 
 fix(persistence): a data step that moves no rows no longer fails the schema upgrade by @RaghavChamadiya in #2738 
 docs: bring the dashboard Architecture and Code Health tab lists up to date by @RaghavChamadiya in #2731 
 fix(mcp): accept get_risk(changed_files=[...]) without targets by @RaghavChamadiya in #2761 
 perf(mcp): read only the targets' graph neighbourhood in get_risk by @RaghavChamadiya in #2763 
 fix(update): stop the first update after init rebuilding every page by @RaghavChamadiya in #2765 
 fix(go): a chained call on an external return type is not a bare-name call by @RaghavChamadiya in #2766 
 fix(go): type a call through a struct field from the field's declaration by @RaghavChamadiya in #2767 
 fix(core): type a nested class's fields and ancestors from its own symbol by @RaghavChamadiya in #2768 
 perf(dead-code): read stored findings instead of re-parsing the repo by @RaghavChamadiya in #2769 
 perf(search): write full-text pages in fixed-size chunks by @RaghavChamadiya in #2780 
 fix(cpp): a static function in another translation unit is not a call target by @RaghavChamadiya in #2770 
 fix(java): record package-private access instead of public by @RaghavChamadiya in #2771 
 fix(typescript): give object-literal methods their own symbol by @RaghavChamadiya in #2772 
 fix(python): resolve super() calls through the MRO, not the file's last same name by @RaghavChamadiya in #2773 
 fix(cpp): a function that returns a pointer or a reference is a symbol by @RaghavChamadiya in #2774 
 fix(core): a parameter or local shadows a bare call's module-level target by @RaghavChamadiya in #2775 
 refactor(actions): build RepoFacts from plain rows in a pure core builder by @RaghavChamadiya in #2752 
 fix(go): type a local from the call that declares it by @RaghavChamadiya in #2777 
 fix(csharp): resolve calls between fragments of a partial class by @RaghavChamadiya in #2776 
 fix(go): type a range loop variable from the container it walks by @RaghavChamadiya in #2778 
 fix(core): resolve a member call once, by its receiver first by @RaghavChamadiya in #2779 
 fix(rust): type a receiver from its annotation or constructor call by @RaghavChamadiya in #2800 
 docs(mcp): list every opt-in tool and stop calling workspace tools automatic by @RaghavChamadiya in #2759 
 docs(languages): match the extension and import-resolution rows to the language specs by @RaghavChamadiya in #2760 
 docs(health): document lazy_load_in_loop, current marker counts and a split_file id limit by @RaghavChamadiya in #2815 
 ci: send unit test coverage to the pull request bot by @RaghavChamadiya in #2809 
 fix(core): give each Java and C# overload its own symbol by @RaghavChamadiya in #2811 
 fix(health): name the opportunity lookup flag found, not resolved by @RaghavChamadiya in #2812 
 fix(cli): read the stored refactoring queue for health --refactoring-targets by @RaghavChamadiya in #2813 
 fix(health): class schema migrations as tooling in the performance context by @RaghavChamadiya in #2814 
 fix(refactoring): credit the share of a finding a plan actually removes by @RaghavChamadiya in #2816 
 fix(perf): a C# task read after it was awaited does not block by @RaghavChamadiya in #2823 
 feat(health): store each file's code origin and per-function dispatch and deprecation facts by @RaghavChamadiya in #2820 
 feat(health): one Fix first queue across defect, maintainability and performance by @RaghavChamadiya in #2821 
 fix(php): a name that only appears in a docblock does not form an import cycle by @RaghavChamadiya in #2824 
 fix(java): refuse a call on a receiver typed to a library class by @RaghavChamadiya in #2827 
 fix(cpp): give each C++ overload its own symbol by @RaghavChamadiya in #2829 
 fix(refactoring): give every plan writer the community labels a full index uses by @RaghavChamadiya in #2830 
 fix(health): keep finding triage across re-index by @RaghavChamadiya in #2819 
 feat(health): rank verification tests by how directly they exercise the change by @RaghavChamadiya in #2825 
 fix(plugins): carry the Fix first wording into the shared code-health skill source by @RaghavChamadiya in #2836 
 fix(dead-code): link Lambda handlers named in serverless, SAM and Terraform config by @RaghavChamadiya in #2834 
 fix(rust): resolve module paths and brace-group imports inside a crate by @RaghavChamadiya in #2835 
 fix(csharp): type each link of a chained call from the one before by @RaghavChamadiya in #2833 
 feat(performance): one opportunity per place you change, ranked by value by @RaghavChamadiya in #2817 
 feat(ui): lead Code Health with Fix first and put the code in the plan drawers by @RaghavChamadiya in #2831 
 fix(ui): give the unknown and no-strategy exclusions their words in Fix first by @RaghavChamadiya in #2838 
 feat(ui): plot the whole filtered set on the Findings impact and effort graph by @RaghavChamadiya in #2832 
 feat(health): Fix first applies the baseline precision levers and says why in plain words by @RaghavChamadiya in #2839 
 fix(health): close out Fix first: perf lines, refactoring default scope, plain text by @RaghavChamadiya in #2841 
 fix(mcp): say what get_dead_code's summary counts by @RaghavChamadiya in #2842 
 feat(core): render the action and Fix-first agent prompts in core by @RaghavChamadiya in #2843 
 fix(mcp): tell the agent to restart a server whose loaded code predates the checkout by @RaghavChamadiya in #2844 
 fix(mcp): run the tests under a reached conftest instead of recommending the conftest by @RaghavChamadiya in #2845 
 feat(mcp): move tool selection into core and add an available_when predicate by @RaghavChamadiya in #2846 
 fix(workspace): skip .NET test projects in contract extraction by @ybai08 in #2828 
 fix(risk): normalize target before dependency lookup by @nightcityblade in #2840 
 fix(java): record canonical constructor takes the record's own access level by @wanjinhao1 in #2798 
 fix(cli): don't pin the workspace root's own DB as the shared store by @nathanpride in #2524 
 fix(sessions): keep a matched rg path even at the repo root by @drakeo338 in #2639 
 fix(health): surface a fetch error in TestsReachingList by @drakeo338 in #2632 
 fix(doc-drift): treat a reader-project path as uncheckable by @Aman-goel-04 in #2802 
 fix(cli): warn when init --resume reuses pages without populating decisions ( #670 ) by @rishu685 in #2482 
 feat(health): show what other lenses hold for a file in the health drawers by @RaghavChamadiya in #2847 
 feat(mcp): one next-call shape for actions, Fix first, health summaries and get_risk by @RaghavChamadiya in #2849 
 feat(ui): one shared prompt preamble, a Verify block everywhere, and Ask in chat from the prompt modal by @RaghavChamadiya in #2848 
 refactor(dead-code): serve findings from a session-free core module by @RaghavChamadiya in #2851 
 fix(objectivec): a static function in another .m file is not a call target by @lesbass in #2837 
 ci: let every push to main finish instead of cancelling the previous run by @RaghavChamadiya in #2826 
 refactor(refactoring): move the pure serving half into core and keep the queue rules as data by @RaghavChamadiya in #2850 
 fix(flows): stop labeling mention-only endings as confidence_filtered by @IdiotCoffee in #2714 
 refactor(health): split the work queue builder, name the recent-regression conditions, cover the chat adapter by @RaghavChamadiya in #2854 
 refactor(performance): move the pure serving half into core and keep the queue rules as data by @RaghavChamadiya in #2852 
 fix(mcp): make AvailabilityFacts hashable as its frozen dataclass promises by @RaghavChamadiya in #2858 
 feat(ui): show the Do next and Fix first agent prompts that core renders by @RaghavChamadiya in #2859 
 perf(update): read the stored vector width from a record, not LanceDB by @RaghavChamadiya in #2861 
 fix(refactoring): give split_file the same commit sets on a re-score as on a full index by @RaghavChamadiya in #2856 
 perf(persist): flush bulk upserts in batches and release the inserted rows by @RaghavChamadiya in #2864 
 perf(health): walk each file's tree once for every whole-file complexity pass by @RaghavChamadiya in #2865 
 perf(security-scan): mask comments and strings once, only when a pattern can match by @RaghavChamadiya in #2866 
 perf(git): share one blame entry per commit instead of one per line by @RaghavChamadiya in #2867 
 perf(search): cap LanceDB's metadata cache so generation memory stops climbing by @RaghavChamadiya in #2868 
 perf(graph): release the symbol subgraph copy once its two kernels have scored it by @RaghavChamadiya in #2869 
 perf(health): release each file's dataflow parse after it is evaluated by @RaghavChamadiya in #2870 
 fix(health): pick a file's lead finding the same way on every run by @RaghavChamadiya in #2872 
 fix(generation): stop SCC pages from archiving a spurious version on init by @RaghavChamadiya in #2873 
 perf(persist): bulk-insert new checkpoint rows and give SQLite a larger page cache by @RaghavChamadiya in #2874 
 feat(contracts): classify what a signature change does to callers by @RaghavChamadiya in #2620 
 feat(change-risk): scope the health delta to the paths a caller names by @RaghavChamadiya in #2621 
 perf(health): tokenize and verify clones without per-token objects by @RaghavChamadiya in #2878 
 fix(health): classify IO imports the same way on every run by @RaghavChamadiya in #2871 
 fix(dead-code): stop file age lifting members of a path-loaded set by @RaghavChamadiya in #2750 
 fix(refactoring): honour the finding registry and never lead with a test file by @RaghavChamadiya in #2751 
 perf(init): time every init stage and take three serial waits off its critical path by @RaghavChamadiya in #2875 
 perf(vector-store): write generated embeddings in a few large batches by @RaghavChamadiya in #2880 
 fix(workspace): route Postgres-backed watch/update through the shared DB instead of local wiki.db by @Aman-goel-04 in #2160 
 fix(init): resume regenerates a page whose vector landed but whose row did not by @RaghavChamadiya in #2883 
 fix(mcp): trim get_change_risk docstring under the schema budget by @RaghavChamadiya in #2925 
 feat(identity): tell people, coding agents and bots apart by @RaghavChamadiya in #2754 
 fix(refactoring): resolve opportunities left open by an older plan model by @RaghavChamadiya in #2904 
 fix(update): keep governance findings when health is rescored by @RaghavChamadiya in #2926 
 fix(health): classify generator output, native external libraries, minified trees and build logic by @RaghavChamadiya in #2899 
 fix(core): read PascalCase suite folders, Gradle test fixtures and QA projects as tests by @RaghavChamadiya in #2913 
 fix(health):

[... truncated for safety ...]

</details>