---
id: inbox_3aabee7d
date: 2026-10-20
source_ref: "[[00-inbox/2026-10-20/0006-gitnexus-releases-rc-01af833875cad5d2374ed988a39b77ff5f9e7-119d]]"
title: "rc/01af833875cad5d2374ed988a39b77ff5f9e716e: fix(scope): preserve lexical bindings in HTTP wrapper detection (#3632)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F01af833875cad5d2374ed988a39b77ff5f9e716e
source: gitnexus-releases
published_at: 2026-10-20T10:36:06+00:00
fetched_at: 2026-10-21T00:12:18.775422+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 GitNexus 的 HTTP wrapper 偵測正確追蹤變數綁定，避免誤判出假路由。 **Why** 包裝式寫入（如 `(app as T) = x`、`app!`）原本會讓 Express 來源資訊在寫入後殘留，產生錯誤的 route。 **How** 寫入失效與共用 pattern walker 改為穿透括號、as/satisfies 與非空斷言；另處理 overload 簽章、declarator 清單與 barrel re-export 的 wrapper 身份遺失問題，並把新增的遞迴遍歷改為 explicit stack。 **What** GitNexus rc 提交，對應 PR #3632（追蹤 #3630），附 regression tests 與 432 檔凍結語料的 call-graph 比對；比對報告為僅一個 CALLS 目標改變、431 CALLS 與 11 METHOD_OVERRIDES 不變，校準後 scaling 報告顯示候選版在 4x 輸入下正規化值皆 ≤1.32（門檻 1.8）。"
key_points:
  - "`(app)`、`(app as T) = x`、`app!` 的賦值與 `app = x` 視為同一綁定的寫入，修正 Express provenance 殘留造成的假 route"
  - "修正 overload 簽章、declarator 清單、barrel re-export 三種 wrapper 身份遺失；另修 HOC、CommonJS 匯出與 node-fetch 等 fetch 套件判斷"
  - "以 explicit stack 取代遞迴，解決 20,000 層解構與 50,000 模組 re-export 鏈的 RangeError；baseline 的 nested-helper-chain 在 4x 輸入正規化值為 14.05，候選版 ≤1.32"
tags: [call-graph, typescript, static-analysis, express, perf-benchmark]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/01af833875cad5d2374ed988a39b77ff5f9e716e: fix(scope): preserve lexical bindings in HTTP wrapper detection (#3632)

讓 GitNexus 的 HTTP wrapper 偵測正確追蹤變數綁定，避免誤判出假路由。

**Why** 包裝式寫入（如 `(app as T) = x`、`app!`）原本會讓 Express 來源資訊在寫入後殘留，產生錯誤的 route。

**How** 寫入失效與共用 pattern walker 改為穿透括號、as/satisfies 與非空斷言；另處理 overload 簽章、declarator 清單與 barrel re-export 的 wrapper 身份遺失問題，並把新增的遞迴遍歷改為 explicit stack。

**What** GitNexus rc 提交，對應 PR #3632（追蹤 #3630），附 regression tests 與 432 檔凍結語料的 call-graph 比對；比對報告為僅一個 CALLS 目標改變、431 CALLS 與 11 METHOD_OVERRIDES 不變，校準後 scaling 報告顯示候選版在 4x 輸入下正規化值皆 ≤1.32（門檻 1.8）。

### 重點
- `(app)`、`(app as T) = x`、`app!` 的賦值與 `app = x` 視為同一綁定的寫入，修正 Express provenance 殘留造成的假 route
- 修正 overload 簽章、declarator 清單、barrel re-export 三種 wrapper 身份遺失；另修 HOC、CommonJS 匯出與 node-fetch 等 fetch 套件判斷
- 以 explicit stack 取代遞迴，解決 20,000 層解構與 50,000 模組 re-export 鏈的 RangeError；baseline 的 nested-helper-chain 在 4x 輸入正規化值為 14.05，候選版 ≤1.32

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F01af833875cad5d2374ed988a39b77ff5f9e716e)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

docs(scope): clarify lexical binding ownership and wrapper provenance 
 
 Checkpoint for #3630 . Publishing the implemented source, regression tests, and benchmark harness as a draft PR; full-suite and final scaling validation remain in progress. 
 
 
 fix(scope): publish #3630 docs/plans 
 
 
 fix(scope): publish #3630 gitnexus/bench/lexical-binding-provenance 
 
 
 fix(scope): publish #3630 gitnexus/bench/lexical-binding-provenance/fixtures 
 
 
 fix(scope): publish #3630 gitnexus/bench/lexical-binding-provenance/results 
 
 
 fix(scope): publish #3630 gitnexus/src/core/ingestion 
 
 
 fix(scope): publish #3630 gitnexus/src/core/ingestion/languages/typescript 
 
 
 fix(scope): publish #3630 gitnexus/src/core/ingestion/languages 
 
 
 fix(scope): publish #3630 gitnexus/src/core/ingestion/pipeline-phases 
 
 
 fix(scope): publish #3630 gitnexus/src/core/ingestion/route-extractors 
 
 
 fix(scope): publish #3630 gitnexus/src/core/ingestion/workers 
 
 
 fix(scope): publish #3630 gitnexus/test/fixtures/lang-resolution/fetch-wrapper-target-identity/lib 
 
 
 fix(scope): publish #3630 gitnexus/test/fixtures/lang-resolution/fetch-wrapper-target-identity 
 
 
 fix(scope): publish #3630 gitnexus/test/fixtures/lang-resolution/fetch-wrapper-target-identity/packages/http 
 
 
 fix(scope): publish #3630 gitnexus/test/fixtures/lang-resolution/fetch-wrapper-target-identity/packages/http/src 
 
 
 fix(scope): publish #3630 gitnexus/test/fixtures/lang-resolution/fetch-wrapper-target-identity/server 
 
 
 fix(scope): publish #3630 gitnexus/test/fixtures/lang-resolution/fetch-wrapper-target-identity/web 
 
 
 fix(scope): publish #3630 gitnexus/test/integration/resolvers 
 
 
 fix(scope): publish #3630 gitnexus/test/unit 
 
 
 fix(scope): publish #3630 gitnexus/test/unit/group 
 
 
 fix(scope): publish #3630 gitnexus/test/unit/scope-resolution 
 
 
 fix(scope): publish #3630 gitnexus/test/unit/scope-resolution/typescript 
 
 
 fix(scope): publish #3630 gitnexus-shared/src/scope-resolution 
 
 
 fix(scope): treat wrapped assignment targets as writes 
 
 
 (app) = new Map() , (app as T) = x and app! = x assign the same binding as 
 app = x , but route-fact invalidation and the shared pattern walker stopped at 
the wrapper, so Express provenance survived the write and produced a false 
route. Recurse through parenthesized, as/satisfies and non-null targets. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(routes): resolve wrappers through overloads, declarator lists and barrels 
 
 Three wrapper shapes lost their identity: 
 
 Bodyless overload signatures were indexed as separate definitions sharing 
the implementation's binding, so the binding looked ambiguous and both local 
and imported calls were rejected. Signatures now declare no callable. 
 Facts for const base = 0, request = (url) =&gt; fetch(url) followed the first 
declarator. The captured name now selects its own declarator. 
 An import resolved to a workspace barrel stopped at index.ts. Workers now 
record named, star and imported-then-exported re-exports, and resolution 
follows them to the declaring module: local and named exports shadow 
 export * , star exports never carry default , and conflicting star exports 
block the name. No repository-wide name fallback is restored. 
 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 test(scope): assert closure ownership against the declaration 
 
 The closure-write assertion compared one lookup with itself, which also passes 
when both are undefined. Compare it with the outer declaration and the shadowing 
parameter, and keep the memoization check explicit. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 refactor(routes): share lexical helpers and release per-file HTTP contexts 
 
 
 Share binding keys, parameter patterns and transparent expression wrappers 
from lexical-bindings instead of four local copies; drop the unused 
moduleStem export; name the inferred-source predicates in lookup. 
 Key the per-file HTTP context by its tree rather than its ParsedFile. 
Workers retain ParsedFiles for the whole chunk, which kept every file's AST 
and traversal maps alive until the chunk flushed. 
 Index re-exports by name, memoize barrel walks per starting export, and keep 
facts without import targets as-is instead of copying them. 
 Move TS-only wrapper cases into the TS describe.each instead of branching 
inside the per-language loop. 
 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(routes): keep wrapper identity for HOCs, CommonJS, object keys and fetch packages 
 
 Four definition shapes that main linked by name lost their wrapper identity: 
 
 const load = useCallback((url) =&gt; fetch(url)) and curried HOCs produced no 
facts because definition lookup stopped at the call; it now follows the 
callable argument, as the structural definition capture does. 
 module.exports = { request } , exports.x = ... and module.exports.x = ... 
were not exports, so destructured require callers missed the wrapper. 
CommonJS export assignments are recorded when module / exports are the 
unshadowed globals, including functions defined inline in the export object. 
 An object-literal key or method name was resolved as a lexical binding and 
collided with a same-named module wrapper. Only binding identifiers now name 
a definition's binding. 
 import fetch from 'node-fetch' no longer counted as fetch. Imports of known 
fetch implementations (node-fetch, cross-fetch, isomorphic-fetch, the fetch 
member of undici and whatwg-fetch) are fetch evidence again; parameters and 
other local names still are not. 
 
 Reference identifiers are also resolved only when their name is bound to a 
callable or class region; other identifiers cannot add a reachability edge. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 test(routes): drive the forwarding fallback case from data and cover re-export merges 
 
 Replace the boolean-switched forwarding fallback case with table rows instead 
of branching inside the test, and assert that barrel re-export facts survive 
worker sub-batch merges. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 chore(bench): reject stale or dirty call-graph exports 
 
 The committed comparison named a candidate revision that is not on this branch, 
and nothing stopped it. Comparison now requires both exports to come from clean 
checkouts and the candidate export to come from the checkout running the 
comparison. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 chore(bench): regenerate the call-graph comparison on the reviewed head 
 
 Clean baseline 565e502 and clean candidate 8a5f7b7 on the frozen 432-file 
corpus (fingerprint 88be1faf...): exactly one CALLS target changes, the 
annotated closure probe declaredOwner.writeAndRead now calls Base.m 
instead of Foo.m . The other 431 CALLS and all 11 METHOD_OVERRIDES edges are 
unchanged. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 chore(bench): emit export provenance and review notes from the comparison 
 
 The comparison report carried export provenance and the expected-change 
explanation only as hand-added fields, which a regeneration dropped. Emit 
both exports' revisions, dirty flags and fingerprints, the unchanged CALLS 
and METHOD_OVERRIDES counts, and an optional --note explanation directly. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 chore(bench): record calibrated scaling reports and the regenerated comparison 
 
 Duration-calibrated-v2 runs (5 warmups, 15 measured batches, 500 ms pilot 
target) pinned to the same CPU, baseline then candidate back to back: 
 
 Baseline 565e502 exceeds the 1.8 normalized ceiling on six arms at 4x 
input: position-index 7.92, position-deep-completed 4.65, nested-helpers 
4.82, nested-helper-chain 14.05, reverse-chain 4.31, name-collisions 2.61 
(medians). 
 Candidate 94f1a05 passes --check: every arm stays at or below 1.32 at 4x 
for both minimum and median, with correct semantic guards on every arm. 
 
 The comparison is regenerated from clean exports with its provenance and 
review note emitted by the tool: one expected CALLS target change, 431 CALLS 
and 11 METHOD_OVERRIDES unchanged. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 refactor(scope): replace recursion with explicit stacks in new traversals 
 
 The binding work added five recursive traversals whose depth follows input 
shape: region summaries (callable nesting), barrel resolution (re-export 
chain length), pattern binding names (destructuring depth), route-fact write 
invalidation (pattern depth), and the position index's max-end tree. Each 
now uses an explicit stack with the same visiting order and results. 
 Regression cases cover the inputs the recursive versions could not handle: 
a 20,000-deep destructuring pattern and a 50,000-module re-export chain both 
threw RangeError before this change. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 perf(routes): avoid a full-tree script walk when building lexical bindings 
 
 Route-fact extraction ran 1.78x slower than main on a 512-function file 
(87 ms vs 49 ms) because createLexicalBindings walked every AST node in script 
to detect collapsed parameter/body environments, which only functions with 
parameter defaults or computed keys can have. 
 
 Find functions with the native type search, skip plain parameter lists 
without any subtree search, and walk only the formals and bodies of the 
rest. Detection is unchanged, except that functions inside syntax-error 
regions are now also checked, which can only add fail-closed ambiguity. 
 Read each node's id and start position once per lookup instead of 
repeatedly crossing into native getters. 
 
 The same extraction now takes about 56 ms against 51 ms on main. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 perf(routes): walk wrapper evidence with a tree cursor 
 
 The wrapper context visited every node through namedChildren, which 
materializes each child as a SyntaxNode and records a parent edge by node 
id. A tree cursor reads node types and offsets natively, so only the node 
types the handlers inspect become SyntaxNodes. Declared identifiers are 
keyed by start offset, and the walk records the ancestor facts later 
queries need (stored binding, default export, declarator of a name) 
instead of a parent map. 
 On the 512-wrapper scaling input, context construction drops from about 
58 ms to 48 ms. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 chore(bench): regenerate the call-graph comparison on the cursor walk 
 
 The candidate export at 6061ca7 has the same fingerprint as the previous 
candidate: the traversal rewrite changes no edge. The one expected target 
change and the 431 unchanged CALLS and 11 METHOD_OVERRIDES remain. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 chore(bench): record final scaling reports on the cursor walk 
 
 Baseline 565e502 and candidate 61de364 ran back to back on CPU 23 
with the duration-calibrated-v2 protocol. Every candidate check stays at 
or below a 1.32 normalized factor against the 1.8 ceiling; the baseline 
fails six of nine arms. Workload fingerprints agree except the documented 
name-collision false positive in the baseline. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 docs(plan): checkpoint the final review, scaling and suite results for #3630 
 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(routes): treat export aliases of one wrapper as one star-export target 
 
 Star-export candidates were deduplicated by the resolved export name, so 
 export { request, request as send } reached through two barrels counted 
as two targets and blocked the import, dropping the consumer's FETCHES 
edge. Candidates are now keyed by the declaration each export name names, 
matching ECMAScript ResolveExport's binding comparison; distinct 
declarations exported under the same name stay ambiguous. 
 Co-Authored-By

[... truncated for safety ...]

</details>