---
id: inbox_a0e8321a
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0101-gitnexus-releases-rc-d8a256a03a101a767dc4e1118913c679af740-f8a6]]"
title: "rc/d8a256a03a101a767dc4e1118913c679af740336: fix(taint): avoid false positives for guarded Git arguments (#3703)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fd8a256a03a101a767dc4e1118913c679af740336
source: gitnexus-releases
published_at: 2026-10-24T14:37:26+00:00
fetched_at: 2026-10-25T01:13:41.429324+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 的 taint 分析減少 guarded Git 參數的誤報，並優化 TypeScript CFG 收集。 **Why** commit 標題指出目標是避免 guarded Git 參數的誤報。 **How** 接受 guard 後細化值域，並沿本地流與函式摘要保留限制；抑制 finding 前檢查完整命令是否符合 sink 用法，未知路徑或預算耗盡時保留保守結果。 **What** 拒絕 destructured/rest 形參的整體證明、減少 TypeScript CFG 的重複 AST 讀取，並附 benchmark 紀錄（refs #3490、#3703）。"
key_points:
  - "guard 被接受後細化值域，並跨本地流與函式摘要傳遞；完整命令不符合 sink 用法時不抑制 finding"
  - "未知路徑或預算耗盡時保留保守 finding；拒絕 destructured/rest 形參的整體證明"
  - "TypeScript CFG 收集減少重複 AST 讀取與配置，並附可攜式 paired benchmark"
tags: [taint-analysis, static-analysis, false-positives, typescript, cfg]
topics: [security, engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/d8a256a03a101a767dc4e1118913c679af740336: fix(taint): avoid false positives for guarded Git arguments (#3703)

GitNexus 的 taint 分析減少 guarded Git 參數的誤報，並優化 TypeScript CFG 收集。 **Why** commit 標題指出目標是避免 guarded Git 參數的誤報。 **How** 接受 guard 後細化值域，並沿本地流與函式摘要保留限制；抑制 finding 前檢查完整命令是否符合 sink 用法，未知路徑或預算耗盡時保留保守結果。 **What** 拒絕 destructured/rest 形參的整體證明、減少 TypeScript CFG 的重複 AST 讀取，並附 benchmark 紀錄（refs #3490、#3703）。

### 重點
- guard 被接受後細化值域，並跨本地流與函式摘要傳遞；完整命令不符合 sink 用法時不抑制 finding
- 未知路徑或預算耗盡時保留保守 finding；拒絕 destructured/rest 形參的整體證明
- TypeScript CFG 收集減少重複 AST 讀取與配置，並附可攜式 paired benchmark

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fd8a256a03a101a767dc4e1118913c679af740336)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(taint): refine values after accepted guards 
 
 Preserve bounded value restrictions through local flows and function 
summaries. Check the complete command against the modeled sink use 
before suppressing a finding. Unknown paths and exhausted budgets 
retain conservative findings. 
 Refs #3490 
 
 fix(taint): preserve guard proof identities 
 
 Reject destructured/rest formals before they inherit a whole-argument 
proof, and include transitive alias uses in bounded guard certificates. 
 Add worker regressions, argument-heavy scaling coverage and global 
refinement fallback diagnostics. 
 Refs #3703 
 
 perf(cfg): reuse scope and argument facts 
 
 Reduce duplicate native AST reads and allocation in TypeScript CFG collection 
while preserving argument forwarding and malformed-input recovery. 
 Add regression cases and a portable paired benchmark with recorded results. 
 
 test(cfg): distinguish validator cases 
 
 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>