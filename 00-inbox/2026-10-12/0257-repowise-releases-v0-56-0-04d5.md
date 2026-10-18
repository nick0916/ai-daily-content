---
id: inbox_953613e7
source: repowise-releases
source_type: rss
url: "https://github.com/repowise-dev/repowise/releases/tag/v0.56.0"
author: "github-actions[bot]"
published_at: 2026-10-12T03:58:01+00:00
fetched_at: 2026-10-18T02:57:00.741988+00:00
content_hash: "04d5d1e99d84b7cc14b9675ea8cf73393ad1eee9b3390d226e004a3394303eb5"
lang: en
caption_quality: None
raw: true
topics: []
---

# v0.56.0

What's Changed 
 
 docs(plugin): say what the Claude Code plugin runs and what leaves the machine by @RaghavChamadiya in #3041 
 release(vscode): 0.11.0 by @RaghavChamadiya in #3042 
 fix(plugin): pass the plugin directory's checks by @RaghavChamadiya in #3043 
 fix(tests): remove claude plugin manifest claim from COUNT_CLAIMS by @justonemorenight in #3045 
 fix(workspace): queue missing-fingerprint reindex under a shared database by @mvanhorn in #3044 
 fix(persistence): loosen PostgreSQL columns at startup so Docker upgrades need no Alembic step by @RaghavChamadiya in #3068 
 fix(decisions): say how many decisions were kept from how many candidates by @RaghavChamadiya in #3088 
 fix(answer): give reasoning models room to write the synthesized answer by @RaghavChamadiya in #3094 
 feat(update): index uncommitted work with repowise update --working-tree by @RaghavChamadiya in #3095 
 fix(risk): pair FooTest.java, FooTests.cs and FooSpec.kt with their source by @RaghavChamadiya in #3096 
 feat(context): add the skeleton+ view: every signature with its lines and all non-function code by @RaghavChamadiya in #3097 
 fix(mcp): resolve Class.method and bare unique names the same way everywhere by @RaghavChamadiya in #3099 
 ci: run unit tests across all runner cores with pytest-xdist by @RaghavChamadiya in #3098 
 fix(mcp): stop searches waiting 30s for a readiness signal nothing tracks by @RaghavChamadiya in #3115 
 feat(risk): list the test files a change will probably need to edit by @RaghavChamadiya in #3101 
 fix(answer): keep the retrieval ranking first in keyless citations by @RaghavChamadiya in #3102 
 perf(update): skip history and analysis phases on a working-tree-only update by @RaghavChamadiya in #3107 
 feat(answer): serve a compact ranked shortlist on low and keyless answers by @RaghavChamadiya in #3108 
 fix(editor-files): steer agents correctly on keyless indexes and mid-edit by @RaghavChamadiya in #3109 
 feat(answer): rank files named in a stack trace or by identifier in the question first by @RaghavChamadiya in #3116 
 fix(tests): count keyless candidate_files the way the citation rule serves them by @RaghavChamadiya in #3122 
 fix(mcp): mark served targets with uncommitted edits instead of calling them fresh by @RaghavChamadiya in #3100 
 refactor(risk): one test list and no empty families in the get_risk PR directive by @RaghavChamadiya in #3117 
 perf(risk): serve the PR blast radius only on request by @RaghavChamadiya in #3118 
 fix(risk): stop risk summaries from overstating or understating a change by @RaghavChamadiya in #3123 
 refactor(risk): drop the uncalibrated structural score from get_risk replies by @RaghavChamadiya in #3124 
 docs(mcp): tighten the search_codebase docstring by @RaghavChamadiya in #3125 
 feat(search): rank files the query names first and return an exact symbol alone by @RaghavChamadiya in #3127 
 feat(mcp): list every edit site of a symbol, verified against live files by @RaghavChamadiya in #3126 
 feat(mcp): accept a grep-style pattern argument as the search query by @RaghavChamadiya in #3128 
 feat(search): name the matching symbols and lines inside each file hit by @RaghavChamadiya in #3130 
 feat(search): return matching source lines for identifier and literal queries by @RaghavChamadiya in #3131 
 feat(mcp): tell agents when to reach for repowise instead of a text search by @RaghavChamadiya in #3134 
 feat(symbol): outline a large class instead of returning its whole body by @RaghavChamadiya in #3136 
 feat(answer): serve a ranked file list when keyless retrieval is weak by @RaghavChamadiya in #3137 
 feat(context): keep only the target symbol's body in a symbol skeleton by @RaghavChamadiya in #3135 
 fix(change-risk): floor and cap the 'bigger than N%' percentile at 99 by @Nehant14 in #3120 
 fix(gemini): drop additionalProperties from tool schemas by @mercael91 in #3064 
 fix(test-paths): count mocks anywhere and the other .NET test-project suffixes by @ybai08 in #2669 
 fix(health): a repo with no scored file has no score, not 10.0 by @swati510 in #3053 
 docs(reference): add the API facts OpenAPI cannot carry by @sloemo01 in #2342 
 fix(test-paths): classify Perl-style t/ as a Python test tree ( #2962 ) by @soumojit-D48 in #3046 
 fix(go): capture a generic call written with explicit type arguments by @ybai08 in #2992 
 fix(uninstall): list and remove the post-commit hook that init installs by @Aman-goel-04 in #2655 
 fix(ingestion): support comments in tsconfig.json and jsconfig.json ( #3058 ) by @rishu685 in #3067 
 fix(providers): default anthropic and claude_cli to claude-haiku-5-5 by @sammcj in #3093 
 fix(cli): drop a stale embedding_model pin when init resolves none by @Aman-goel-04 in #2654 
 fix(health): stop knowledge_loss firing on a pure-rename-only commit window by @Aman-goel-04 in #3075 
 fix(mcp): stop watchdog walk at unnamed or dead ancestor by @Aman-goel-04 in #3142 
 fix(mcp): anchor fix history recency to indexed commit instead of wall clock ( #3110 ) by @rishu685 in #3145 
 fix(generation): sort wiki backlinks deterministically before applying cap ( #2792 ) by @rishu685 in #2881 
 fix(editor-files): separate the confidence and scope sentences in the CLAUDE.md/AGENTS.md header ( #3103 ) by @tecsmurf in #3144 
 feat(web): i18n foundation (next-intl + English fallback + catalog gates) by @limitcool in #3129 
 feat(web): add the zh-CN catalog and the language switcher by @limitcool in #3151 
 refactor(providers): share one base for agent CLI providers by @RaghavChamadiya in #3167 
 feat(providers): declare every LLM provider once, as a ProviderSpec by @RaghavChamadiya in #3168 
 feat(agents): add the Basic tier and an Indexing column by @RaghavChamadiya in #3169 
 feat(init): default the provider picker to the agent you use by @RaghavChamadiya in #3171 
 fix(settings): read provider, embedder and price facts from the server by @RaghavChamadiya in #3172 
 feat(agents): add GitHub Copilot CLI and Kiro targets, Copilot instructions for VS Code by @RaghavChamadiya in #3173 
 docs(agents): add the agent platform recipe for contributors by @RaghavChamadiya in #3178 
 feat(agents): rewrite Cursor shell commands through a preToolUse hook by @RaghavChamadiya in #3177 
 fix(mcp): accept a query argument as the symbol id in get_symbol by @RaghavChamadiya in #3140 
 fix(search): match path queries against filename words by @RaghavChamadiya in #3180 
 fix(answer): lead the keyless answer with the top retrieval file by @RaghavChamadiya in #3184 
 fix(answer): trim keyless medium answers on large repos by @RaghavChamadiya in #3186 
 fix(context): cap one file's reference sites so a mock-heavy test cannot flood the list by @RaghavChamadiya in #3183 
 feat(graph): bind names destructured from a dynamic import() by @RaghavChamadiya in #3181 
 feat(search): return the best-matching lines for prose queries by @RaghavChamadiya in #3189 
 fix(doctor): join the stderr drain before building the crash detail by @Pushpak731 in #3165 
 fix(context): follow a local import alias in the references edit set by @RaghavChamadiya in #3190 
 fix(search): cap one file's line hits so test mocks cannot flood an identifier search by @RaghavChamadiya in #3191 
 fix(search): start snippets at the page text, not its heading by @RaghavChamadiya in #3192 
 feat(search): surface symbols whose name words match a prose query by @RaghavChamadiya in #3194 
 feat(context): list callers through forwarding wrappers by @RaghavChamadiya in #3195 
 feat(graph): record functions passed as values so registrations show as callers by @RaghavChamadiya in #3197 
 fix(change-risk): trim redundant MCP response fields by @Nehant14 in #3152 
 fix(mcp): don't create a stray .repowise/ when the store is missing by @inchang-ing in #3166 
 fix(search): drop page_id when page_type + path rebuild it by @SatvikMishra08 in #3156 
 fix(search): bound line hits when a search mixes words and identifiers by @RaghavChamadiya in #3199 
 feat(answer): answer caller and trigger questions from the call graph by @RaghavChamadiya in #3196 
 fix(mcp): retain fallback_targets not named in emitted answer rows ( #2900 ) by @rishu685 in #2995 
 feat(search): return files that have no wiki page by @RaghavChamadiya in #3210 
 fix(search): scan the whole repo for literal and identifier line hits by @RaghavChamadiya in #3201 
 feat(context): show the calling line on caller rows by @RaghavChamadiya in #3198 
 feat(answer): retrieve files that have no wiki page by @RaghavChamadiya in #3214 
 feat(answer): show who uses the lead file on impact questions by @RaghavChamadiya in #3212 
 fix(mcp): trim get_risk card responses and move detailed owner metrics behind owners include ( #3112 ) by @rishu685 in #3139 
 fix(health): do not charge a sink in a generator or iterator closure to its caller by @Aman-goel-04 in #3003 
 fix(health): name an Extract Method helper in the file's language by @chaitanya-y20 in #2895 
 fix(health): exempt Java try ... fail() expected-exception idiom from swallowed_catch ( #2890 ) by @rishu685 in #2996 
 fix(security): rescan every file when the scanner version changes by @Aman-goel-04 in #3086 
 fix(health): classify each leaf of a grouped Rust use statement on its own by @Aman-goel-04 in #3076 
 fix(health): respect in-source # noqa suppression comments on Python except lines ( #2745 ) by @rishu685 in #2853 
 fix(ingestion): ignore TypeScript type-only imports in dependency cycle detection ( #2742 ) by @rishu685 in #2803 
 fix(health): exclude dynamic_uses hint edges from cycle detection by @Aman-goel-04 in #3077 
 fix(mcp): redirect no_such_path to a renamed or split file by @Aman-goel-04 in #2922 
 fix(security): ignore documented placeholder credentials by @abhinavrastogi2627 in #3179 
 test(security): compare masking runtime growth by @kudala-bharani in #3203 
 feat(health): promote PHP to Good tier with complexity, LCOM4, and assertion block support ( #3065 )... by @rishu685 in #3089 
 fix(core): a test-named module pytest does not collect is not a test by @RaghavChamadiya in #3218 
 fix(ingestion): index source packages named build, coverage, dist or target by @RaghavChamadiya in #3221 
 feat(impacted-tests): select a subset when the index lags the change's base by @RaghavChamadiya in #3219 
 feat(ingestion): link modules named by string in lazy registries by @RaghavChamadiya in #3220 
 feat(impacted-tests): run tests the graph cannot see into with every subset, and --explain by @RaghavChamadiya in #3217 
 feat(impacted-tests): give each runner only its own always-run tests and name the rest by @RaghavChamadiya in #3241 
 fix(health): one perf plan step per call site, naming the call it batches by @RaghavChamadiya in #3250 
 fix(health): gate Extract Method plans on span share, size and docstring start by @RaghavChamadiya in #3252 
 fix(health): keep dormant and dead code out of Fix first and the perf queue by @RaghavChamadiya in #3253 
 fix(health): mark Extract Method spans that await as async helpers by @RaghavChamadiya in #3254 
 fix(health): find import cycles over runtime edges and make break_cycle advisory by @RaghavChamadiya in #3259 
 fix(health): ternary dispatch chains and JSX conditionals do not nest by @RaghavChamadiya in #3278 
 fix(health): name a perf step's function and mark async extractions in Fix first steps by @RaghavChamadiya in #3273 
 fix(selection): wire test setup files and path-named helpers into the graph by @RaghavChamadiya in #3216 
 feat(impacted-tests): scope manifest, package-init and asset triggers instead of running every test by @RaghavChamadiya in #3243 
 feat(selection): narrow a conftest reached only through its imports by @RaghavChamadiya in #3262 
 fix(health): keep migrations, startup, shutdown and recovery out of the perf queue by @RaghavChamadiya in #3258 
 fix(actions): add tests only where no test reaches; stand history rules down on a short history by @RaghavChamadiya in #3266 
 fix(refactoring): list the tests that 

[... truncated for safety ...]