---
id: inbox_ac671713
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-gitnexus-releases-rc-2b6542737ad5dfb63b720695c77643282bd69-68af]]"
title: "rc/2b6542737ad5dfb63b720695c77643282bd6932a: fix(go): resolve imports within selected modules (#3654)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F2b6542737ad5dfb63b720695c77643282bd6932a
source: gitnexus-releases
published_at: 2026-10-21T18:24:18+00:00
fetched_at: 2026-10-21T23:45:10.278556+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 修正 Go 解析器的 import 解析：改為讀取倉庫內所有 go.mod 與 go.work，避免不同模組的同名套件被錯配。 **Why** 原本只讀根目錄的 go.mod；沒有根 go.mod 時，所有 import 都走 GOPATH 後綴匹配，兩個模組的 internal/repository 會同時對應到同一目標，路徑與目錄不一致的模組（如 github.com/acme/orders 位於 services/orders）則解析為空。 **How** 每個 import 由路徑前綴最長的模組擁有；同路徑的多個 go.mod 依 importer 所在模組與 go.work 的 use 清單消歧，仍無法判定就不解析，GOPATH 後綴匹配只保留給模組外的 importer。 **What** 在 lang-resolution 語料中，既有 CALLS/ACCESSES 邊沒有被移除或改指，新增 70 條；call drops 從 148 降到 135，.go call drops 從 14 降到 1。另外 go.mod 讀取失敗改為拋錯，並以單一 file handle 讀檔以修正 CodeQL 指出的競態問題。"
key_points:
  - "每個 import 由路徑前綴最長的模組擁有；同路徑多 go.mod 時依 importer 模組與 go.work use 清單消歧，無法判定則不解析"
  - "語料測試：既有 CALLS/ACCESSES 邊無移除或改指，新增 70 條；call drops 148 → 135，.go call drops 14 → 1"
  - "go.mod 改用 O_NOFOLLOW、O_NONBLOCK 單一 handle 讀取，讀取失敗改為拋錯而非靜默跳過"
tags: [go, import-resolution, code-intelligence, static-analysis, monorepo, bug-fix]
topics: [engineering.architecture]
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/2b6542737ad5dfb63b720695c77643282bd6932a: fix(go): resolve imports within selected modules (#3654)

GitNexus 修正 Go 解析器的 import 解析：改為讀取倉庫內所有 go.mod 與 go.work，避免不同模組的同名套件被錯配。 **Why** 原本只讀根目錄的 go.mod；沒有根 go.mod 時，所有 import 都走 GOPATH 後綴匹配，兩個模組的 internal/repository 會同時對應到同一目標，路徑與目錄不一致的模組（如 github.com/acme/orders 位於 services/orders）則解析為空。 **How** 每個 import 由路徑前綴最長的模組擁有；同路徑的多個 go.mod 依 importer 所在模組與 go.work 的 use 清單消歧，仍無法判定就不解析，GOPATH 後綴匹配只保留給模組外的 importer。 **What** 在 lang-resolution 語料中，既有 CALLS/ACCESSES 邊沒有被移除或改指，新增 70 條；call drops 從 148 降到 135，.go call drops 從 14 降到 1。另外 go.mod 讀取失敗改為拋錯，並以單一 file handle 讀檔以修正 CodeQL 指出的競態問題。

### 重點
- 每個 import 由路徑前綴最長的模組擁有；同路徑多 go.mod 時依 importer 模組與 go.work use 清單消歧，無法判定則不解析
- 語料測試：既有 CALLS/ACCESSES 邊無移除或改指，新增 70 條；call drops 148 → 135，.go call drops 14 → 1
- go.mod 改用 O_NOFOLLOW、O_NONBLOCK 單一 handle 讀取，讀取失敗改為拋錯而非靜默跳過

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F2b6542737ad5dfb63b720695c77643282bd6932a)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(go): resolve imports against every go.mod in the repository 
 
 The Go resolver read only the repository-root go.mod, and its import 
target ignored the importing file. With no root go.mod, every import took 
the GOPATH suffix match down to a two-segment tail. Two modules' 
 internal/repository then both answered .../internal/repository , and a 
module whose directory differs from its path ( /vN , services/orders 
for github.com/acme/orders ) resolved to nothing. With a root go.mod, 
imports of a nested module were not the root's and dropped, while the 
root module's own packages matched any directory ending in the package 
path, including nested modules' trees. 
 Capture every go.mod and go.work from the scan's path list, as Dart does 
for pubspec.yaml; standalone and rename callers rescan with the same 
walker. For each import, the module whose path is the longest 
 / -prefix owns it. The package is the exact directory under that 
module's root, unless a nested go.mod removes the directory from the 
module. Several go.mod files declaring one path are disambiguated by the 
importer's own module, then by its go.work use list, else left 
unresolved. Unowned imports from inside a module stay unresolved; the 
GOPATH suffix match remains only for importers outside every module. 
 In the combined lang-resolution corpus, no CALLS or ACCESSES edge is 
removed or retargeted against the parent commit, and 70 are added outside 
the two new fixtures. Drops are unchanged at 179: these sites were 
silent. The import-target bench's go arm now passes no module config, 
and its answers and fingerprint are unchanged. The scope-capture go 
fingerprint moves for the new fixtures only. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 perf(go): look up an importer's module only when a path is contested 
 
 locateGoImport walked to the importer's nearest go.mod and go.work for 
every import, though most imports (standard library, dependencies) are owned 
by no in-repo module and need neither, and every candidate package directory 
repeated the same ownership walk. The walks are now lazy (only a module path 
several go.mod files declare consults them) and memoized per directory on 
the config's index, and a path with no backslash skips the normalizing 
replace. The Go package index is fetched once per import instead of per 
candidate directory. 
 Behavior-preserving: the lang-resolution corpus emits the identical 3,002 
CALLS/ACCESSES edges before and after. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(go): surface go.mod read failures instead of dropping the module 
 
 Go's workspace capture skipped any manifest it could not read and turned a 
failed standalone scan into "no modules". Either one silently erases a module 
boundary: its imports then resolve against the enclosing module or fall back 
to GOPATH suffix matching, the misresolution this capture exists to remove, 
and a rename refresh compares a different config against its preview's. 
 captureResolutionConfig requires capture failures to throw. 
 
 A manifest that fails to read now throws; the standalone scan propagates 
its error. 
 Manifests skipped on purpose stay skipped, named in one place: symlinks, 
which can point outside the repository (Dart's manifest capture excludes 
them too), non-files, files over the source-file size cap, and files gone 
since the scan listed them. 
 Manifests are read 32 at a time; capture blocks the scan, and k8s-style 
trees have hundreds of go.mod files. 
 
 Tests: data-driven rows for each skipped shape, a go.mod that fails to read, 
and a standalone scan of a non-directory root. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 test(bench): re-measure Go counts and fingerprint on top of #3651 
 
 Rebased onto main after #3651 . Import resolution across every go.mod clears 
the 13 Go call drops left in the combined corpus (go-chain-call, 
go-grouped-type-decl, go-interface-field-dispatch, 
go-pointer-receiver-field-chain): call drops 148 -&gt; 135, all kinds 208 -&gt; 195, 
.go call drops 14 -&gt; 1. No drop added; shape-arm states unchanged. 
 The scope-capture go fingerprint moves for the two new fixtures only: parking 
them restores main's acee4449f691d9138e68e7b2b19da863fc2c89b0e9846acdf10e93d76b2eec78 
byte-for-byte. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(go): read go.mod through one handle so it cannot change mid-check 
 
 CodeQL flagged the manifest read as a file-system race: lstat checked the 
path and readFile then opened it again, so a different file could be read 
than the one checked. The manifest is now opened once (O_NOFOLLOW refuses a 
leaf symlink, O_NONBLOCK keeps a FIFO from hanging) and its type, size and 
contents all come from that handle, the way Dart's manifest reader works. A 
platform without O_NOFOLLOW still refuses a link after the open. 
 The read-permission test is POSIX-only: permission bits do not block reads 
on Windows. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 test(go): skip the unreadable-go.mod test as root; correct a fixture comment 
 
 Review follow-up for #3654 . 
 
 The permission test asserted EACCES on a mode-000 go.mod, which root can 
still open. It now skips for root as well as on Windows. 
 The orders-service ledger fixture said it shares its method names with 
billing's; only Save is shared. The comment says so, in the same two 
lines. Comment text is part of the Go captures, so the golden gains the 
new text and the scope-capture go fingerprint moves: 
3ba3b6e1551311ddb0e9330c939ac995856b487303b6f64bc89da3689a6d9d2c -&gt; 
b1dfa8e1a8d92fd9d5779a02bc4bd99f54ec87adae4a326be08b74cb48fd5ef3, with 
fixture and group counts unchanged. 
 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
 
 fix(go): enforce module visibility ( #3654 ) 
 
 Limit local providers to the importing module and peers selected by its 
nearest go.work. Treat failed package-qualified receiver lookup as final 
for direct calls, field chains, and method values so bare-name fallback 
cannot recreate calls into independent modules. 
 Add import/call boundary regressions and remeasure receiver drops. The 
same-corpus comparison removes exactly two false calls and adds no edges. 
 Validation: 7,263 resolver tests, both typechecks, lint, and import-target, 
scope-capture, and receiver baseline checks pass. Two parser-identity 
checks affected by local snapshot/build drift pass after freezing inputs 
and rebuilding. The full local run continues; final CI remains required. 
 
 fix(go): reject ambiguous package providers ( #3654 ) 
 
 Check all selected module prefixes for package presence. Preserve a shorter-only provider and refuse imports supplied by multiple modules. Cover all four presence cases and correct the receiver suppression comment. 
 Note: the full local suite hit a host GLIBCXX_3.4.31 failure in parse-cache-identity-package.test.ts; focused Go tests and both TypeScript checks pass. 
 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com

</details>