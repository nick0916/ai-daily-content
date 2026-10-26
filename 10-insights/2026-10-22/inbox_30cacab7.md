---
id: inbox_30cacab7
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-gitnexus-releases-rc-e7ef82dfcb3c794710ef902b292d5e36ddbab-d1c2]]"
title: "rc/e7ef82dfcb3c794710ef902b292d5e36ddbab977: fix(kotlin): type locals from package-qualified factory calls (#3660)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fe7ef82dfcb3c794710ef902b292d5e36ddbab977
source: gitnexus-releases
published_at: 2026-10-22T16:49:06+00:00
fetched_at: 2026-10-23T01:00:36.133033+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓程式碼分析工具能追蹤命名空間工廠函式的回傳型別，補上漏掉的呼叫關係。 **Why** 原本 `x = rp.make()` 會把 x 綁到原始字串 rp.make，導致之後的 x.m() 失去接收者型別而漏掉呼叫邊。 **How** 把 dotted callee 對應到函式的回傳型別註解，Python、Dart、Zig 各自處理命名空間 import；未能解析的情況改為明確記錄為 drop。 **What** Python 接收者基準中 call drops 由 128 增至 151、reads 由 44 增至 48，新增的 drop 都沒有對應的 CALLS edge；完整 lang-resolution corpus 的 2,838 條 CALLS/ACCESSES edge 數量不變。"
key_points:
  - "命名空間工廠呼叫（如 `rp.make()`）依函式回傳型別註解推斷接收者型別，涵蓋 Python、Dart、Zig（標題另列 Kotlin）"
  - "原本靜默丟棄的未型別化呼叫（如 `ns.untyped()`、`s.repo.Delete(id)`）改為記錄為 exact drop，使缺口可見"
  - "只有原本未輸出任何 edge 的位置有變動，完整 corpus 的既有 edge 不變"
tags: [type-resolution, call-graph, static-analysis, python, zig]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/e7ef82dfcb3c794710ef902b292d5e36ddbab977: fix(kotlin): type locals from package-qualified factory calls (#3660)

讓程式碼分析工具能追蹤命名空間工廠函式的回傳型別，補上漏掉的呼叫關係。

**Why** 原本 `x = rp.make()` 會把 x 綁到原始字串 rp.make，導致之後的 x.m() 失去接收者型別而漏掉呼叫邊。

**How** 把 dotted callee 對應到函式的回傳型別註解，Python、Dart、Zig 各自處理命名空間 import；未能解析的情況改為明確記錄為 drop。

**What** Python 接收者基準中 call drops 由 128 增至 151、reads 由 44 增至 48，新增的 drop 都沒有對應的 CALLS edge；完整 lang-resolution corpus 的 2,838 條 CALLS/ACCESSES edge 數量不變。

### 重點
- 命名空間工廠呼叫（如 `rp.make()`）依函式回傳型別註解推斷接收者型別，涵蓋 Python、Dart、Zig（標題另列 Kotlin）
- 原本靜默丟棄的未型別化呼叫（如 `ns.untyped()`、`s.repo.Delete(id)`）改為記錄為 exact drop，使缺口可見
- 只有原本未輸出任何 edge 的位置有變動，完整 corpus 的既有 edge 不變

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fe7ef82dfcb3c794710ef902b292d5e36ddbab977)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(scope): follow namespace factory return types and record untyped drops 
 
 import mod as rp; x = rp.make(); x.m() lost the receiver type even when 
 make is declared -&gt; C : x was bound to the raw dotted name rp.make , 
and nothing followed a dotted name to a function's return type. The inline 
 rp.make().m() failed the same way in the compound resolver, which read 
 ns.f() only as a construction. 
 Resolve ns.f to f 's return annotation when ns is a namespace import, 
the fact propagateImportedReturnTypes already mirrors for a named import. 
The post-finalize chain follow uses it for bindings and the compound 
resolver for inline calls. Only sites that emitted nothing change: the 
full lang-resolution corpus emits the identical 2,838 CALLS/ACCESSES edges. 
 Record the drops that left impact at "exact": 
 
 a plain receiver bound to a namespace function with no usable return type 
( x = ns.untyped() ); 
 an outer call whose file:line:col key a resolved inner site already 
claimed ( ns.untyped().m() , s.repo.Delete(id) ). Only a duplicate 
capture of the same member hides a drop now. 
 
 Receiver baseline: call drops 128 -&gt; 151, reads 44 -&gt; 48, ten shape-arm 
cells INVISIBLE-GAP -&gt; VISIBLE-GAP; every new drop has no CALLS edge to its 
member (BASELINE.md lists them). The python.factory-qualified accuracy gap 
is removed; the python-scope fingerprint and capture golden gain the new 
fixture only. 
 Fixes #3498 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(dart): type locals from prefixed-import factory calls 
 
 import 'mod.dart' as rp; final x = rp.make(); x.m() gave x no type: 
local call inference accepted only a bare callee ( Callee() ), and the 
prefix-stripping type normalizer would have reduced rp.make to make . 
 Bind a local initialized by exactly prefix.member(...) (direct or 
awaited) to the dotted callee and keep its prefix, so the shared chain 
follow types it from the namespace function's return annotation. Only 
call-derived bindings keep the prefix; annotated prefix.Type spellings 
are unchanged. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(zig): type locals from namespace-module factory calls 
 
 const rp = @import("mod.zig"); const x = rp.make(); x.m() bound x to 
the namespace handle rp itself: the call-return rule reads a non-value 
head as the type being constructed ( Counter.init() ), and import bindings 
are not values. The member name was gone before the shared chain follow 
could use the new namespace return-type lookup. 
 For a module-level handle on a lowercase file (a namespace module, by Zig 
convention), bind the dotted callee rp.make so the shared chain follow 
types it from make 's return annotation. File-struct handles 
( @import("Page.zig") , any spelling of the handle) keep naming the 
struct, so Page.init() is unchanged. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 test(bench): rebaseline captures and receiver counts for Dart and Zig 
 
 
 receiver-resolution: the Dart fixture's untyped factory adds one call 
drop (151 -&gt; 152); every typed form in the Dart and Zig fixtures resolves. 
 scope-capture (dart): two existing dart-method-enrichment locals 
initialized by obj.method() / Type.method() gain a call-derived 
binding, plus the new fixture's captures. A full lang-resolution A/B 
emits the identical edges outside the new fixtures. 
 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(scope): bind same-namespace inheritance bases before sibling visibility exists 
 
 Cause: same-package / same-namespace visibility ( populateNamespaceSiblings ) 
is populated after the inheritance pre-pass and buildMro . A base written 
without an import ( class C extends B , B in another file of the package) 
could bind only through the workspace-unique simple-name fallback, which any 
other package declaring a B defeats: no EXTENDS edge, an empty MRO, and 
lost calls through inherited members. In the combined lang-resolution corpus 
 java-grandparent-resolution c.greet().save() dropped because 
 java-unrelated-method-collision declares default-package A and B. 
 Moving the sibling hook ahead of the pre-pass was measured and rejected. It 
retargeted correct edges and minted wrong ones, because the sibling channels 
carry candidates the pre-pass must not see: C# global-namespace types are 
consulted at every scope (same-file Cat : Animal bound another fixture's 
global Animal), namespace buckets merge across source roots with no 
proximity order (PHP, C#), and a qualified extends app.base.Box bound 
through a same-package app.Box . 
 Fix: an optional ScopeResolver.resolveImplicitInheritanceBase , consulted by 
the pre-pass only when the shared chain bound nothing, the base was written 
bare (no qualifier, name capture at the start of the base expression), and 
no import claims the name. It adds edges and never retargets one. 
 resolveSameNamespaceInheritanceBase picks the candidate in the deriving 
class's namespace, nearest by shared path prefix, refusing a tie. Java and 
Kotlin answer from their package facts, C# from the exact namespacePrefix . 
 Corpus A/B (main vs this, same corpus): EXTENDS/IMPLEMENTS +42, all within 
their own fixture, 0 removed. CALLS: six super.save() edges keep their 
target but are now MRO-dispatched ( global , as in isolation), one moves off 
another fixture's BaseModel.Save onto its own, and 7 are new (both 
grandparent greet calls, a default-method validate , the new fixtures). 
Receiver bench: call drops 128 -&gt; 127, all kinds 192 -&gt; 191, shape arm 
unchanged. Scope-capture fingerprints re-baselined for the added fixtures 
only (parked, --check passes on the old ones). 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(java): resolve a duplicated package+type import to the importer's own root 
 
 Cause: buildJavaPackageIndex kept the first file declaring each 
package+type. One repository can hold several build modules or sample 
projects that each declare models.User , so every import models.User; 
bound whichever copy was parsed first, a wrong IMPORTS edge at full 
confidence that carries the receiver types behind it. In the combined 
lang-resolution corpus 24 fixtures declare models.User , and e.g. 
 java-heritage UserService.processUser called 
 java-assignment-chain/models/User.save . 
 Fix: the index keeps every declaring file in a sparse duplicateTypes map 
(only colliding pairs, so a normal workspace pays nothing), and a type import 
resolves to the declaring file sharing the longest leading path with the 
importer (its own module or source root). A tie, or an unknown importer, 
refuses rather than guessing. Wildcard imports are unchanged. 
 Corpus A/B (previous commit vs this, same corpus): 40 CALLS edges that 
crossed into another fixture's User/Repo/Address/UserService are gone, 55 
CALLS/ACCESSES edges now land in their own fixture (0 cross-fixture), and 
 java-parent-resolution User IMPLEMENTS Serializable moves off 
 java-heritage onto its own interface. Receiver-unresolved drops unchanged; 
import-target and receiver benches pass. Scope-capture java fingerprint 
re-baselined for the added fixture only (parked, --check passes on the old 
one). 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 refactor(scope): expose the position a receiver-chain fold reaches 
 
 foldReceiverChain answers "which class", so a chain whose last step is 
declared as a type the program does not contain ( Dictionary&lt;string, User&gt; , String ) reads only as a miss. That miss is informative to the 
receiver-origin classifier: every hop was typed by a program declaration 
and the last one names a library type. 
 Extract the fold loop into foldReceiverChainState and export 
 foldReceiverChainPosition , which returns the final position including 
one whose declared type named no class, and reports nothing to 
 recordReceiverType . foldReceiverChain keeps its behaviour: it now 
wraps the same loop and makes the receiver-type report from the final 
state, as before. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(scope): classify library-rooted receiver drops from provider evidence 
 
 classifyReceiverOrigin had one source of positive external evidence, 
 LanguageProvider.isBuiltInName . That set also filters callee names out 
of the call graph, so it could not grow to cover host globals, stdlib 
imports or library-typed values without dropping real edges, and every 
such drop hedged impact() to lower-bound . It also read a base name as 
evidence even where the program bound that name itself: a parameter 
named console with an unresolved type, or an unresolved import of a 
built-in spelling from the program's own module, came back external . 
 Add two provider data hooks read only by the classifier: 
 externalReceiverNames (globals, platform roots, library types) and 
 isExternalModuleSpecifier (import specifiers reserved for the runtime 
or stdlib). The classifier now answers external when: 
 
 the base is unbound at the site and is a built-in or listed name; 
 the base is bound only by imports that resolved to no program file and 
all name a library module; 
 the receiver chain folds, through declarations each owner makes, to a 
position declared as a library type ( this.data.Keys with 
 Dictionary&lt;string, User&gt; data ), and the program declares nothing by 
the dropped member's name (an extension method or trait impl could be 
the real target). The fold skips ancestor-hoisted bindings, which can 
lend another class's member type to the step. 
A base the program binds (a parameter, a local, a resolved import, an 
import from a non-library module) never takes a name-based verdict. The 
in-program arms are unchanged and still win first. No drop is added or 
removed and no edge changes. 
 
 Java supplies its reserved java package root for both hooks: the JVM 
refuses to define classes under java.* , so java.util.Optional.of(...) 
and import java.util.Map are rooted in the platform. Without the 
specifier hook, the stricter import rule would have demoted the existing 
 import java.util.List; List.of(...) verdict to unknown. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(typescript): name JavaScript host globals as the program boundary 
 
 document.body.appendChild(...) , window.history.pushState(...) and 
 Buffer.from(raw).toString() were recorded unknown : none of 
 document , window , Buffer , process or globalThis is in 
 BUILT_INS , and they cannot be added there because that set also 
filters callee names, so process would drop every call to a program 
function named process . Each drop hedged impact() to lower-bound 
although no program node could have been the target. 
 List the host objects in EXTERNAL_RECEIVER_NAMES and supply it to the 
TypeScript, JavaScript and Vue providers as externalReceiverNames . A 
name counts only where the program binds nothing by it and declares 
nothing by it, so a document: Doc parameter, an untyped window 
parameter, a local navigator and a program class Buffer keep their 
verdicts. location , history , self and crypto stay out: they are 
ordinary local names. 
 Corpus: 5 call drops move from unknown to external. process.env.* 
(3 reads) stays in-program there because three fixtures declare a 
top-level function process() , one of them in a global script. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(python): name standard-library imports as the program boundary 
 
 os.environ.setdefault(...) after import os , and 
 Path(__file__).resolve() after from pathlib import Path , were 
recorded unknown . The imports resolve to no file in the program, but an 
unresolved import alone cannot be told apart from an in-program module 
the resolver missed, and nothing said that os and pathlib belong to 
the interpreter. 
 Supply isExternalModuleSpecifier from a curated set of standard-library 
modules, matched on the specifier's first segment ( os.pa

[... truncated for safety ...]

</details>