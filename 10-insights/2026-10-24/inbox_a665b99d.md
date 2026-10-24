---
id: inbox_a665b99d
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0347-ruflo-releases-v3-61-0-rure-reads-cuda-rure-analyze-cud-6e7b]]"
title: "v3.61.0 — ruRE reads CUDA (rure_analyze_cuda)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.61.0
source: ruflo-releases
published_at: 2026-10-24T03:36:06+00:00
fetched_at: 2026-10-24T03:56:32.980238+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo 新增唯讀 MCP 工具，可在不執行檔案的情況下解析 CUDA 二進位檔。 **How** 只解析 fatbin、cubin、PTX 檔案，不執行內容，檔案中取得的字串會通過 AIDefence 閘門；目前未含 SASS 解碼與 cuobjdump 呼叫。 **What** 新增 rure_analyze_cuda（ruflo-rure 0.5.0），可讀出每個 kernel 的暫存器數、程式碼大小、constant／shared／local 記憶體，以及 PTX 版本與目標架構；已對照 nvcc 12.8 與 13.0 輸出驗證，zstd 項目需 Node 22.15+。"
key_points:
  - "新增 rure_analyze_cuda，讀取 fatbin、cubin、PTX 並回報每個 kernel 的暫存器數與記憶體用量"
  - "已用 nvcc 12.8 與 13.0 的真實輸出驗證；未含 SASS 解碼與 cuobjdump 呼叫"
  - "ruflo-mods 0.7.0 新增 opt-in 的 rureOffer（預設關閉，ADR-498），模型觸碰二進位檔時提示可用 ruRE 檢視"
tags: [ruflo, cuda-static-analysis, mcp-tool, binary-analysis, dependency-audit]
topics: [agents.mcp, security]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.61.0 — ruRE reads CUDA (rure_analyze_cuda)

ruflo 新增唯讀 MCP 工具，可在不執行檔案的情況下解析 CUDA 二進位檔。 **How** 只解析 fatbin、cubin、PTX 檔案，不執行內容，檔案中取得的字串會通過 AIDefence 閘門；目前未含 SASS 解碼與 cuobjdump 呼叫。 **What** 新增 rure_analyze_cuda（ruflo-rure 0.5.0），可讀出每個 kernel 的暫存器數、程式碼大小、constant／shared／local 記憶體，以及 PTX 版本與目標架構；已對照 nvcc 12.8 與 13.0 輸出驗證，zstd 項目需 Node 22.15+。

### 重點
- 新增 rure_analyze_cuda，讀取 fatbin、cubin、PTX 並回報每個 kernel 的暫存器數與記憶體用量
- 已用 nvcc 12.8 與 13.0 的真實輸出驗證；未含 SASS 解碼與 cuobjdump 呼叫
- ruflo-mods 0.7.0 新增 opt-in 的 rureOffer（預設關閉，ADR-498），模型觸碰二進位檔時提示可用 ruRE 檢視

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.61.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Minor release: @claude-flow/cli , claude-flow , ruflo 3.61.0. Adds one MCP tool ( rure_analyze_cuda ). No leaf package changed, so no standalone publishes. 
 Added 
 
 ruRE: CUDA static analysis (ruflo-rure 0.5.0, plugin ADR-0006). New read-only MCP tool rure_analyze_cuda reads the GPU code inside a CUDA fatbin, cubin or PTX file: fatbin entries (PTX or cubin, target architecture, LZ4/zstd compression), each kernel with register count, code size and constant/shared/local memory, and PTX version, target and kernel names. It parses only; nothing is executed, and strings taken from the file pass the AIDefence gate. Checked against real nvcc 12.8 and 13.0 output. Not included: SASS decoding, cuobjdump shell-out. zstd entries need Node 22.15+. 
 ruflo-console 0.47.0: a CUDA row on the ruRE page, DETECT routes for .cubin , .fatbin and .ptx , and a hint on a native binary that holds a CUDA fatbin (ADR-495..497). The ruRE page refuses a sample that is a symlink, wraps long lists, and shows Claude a structured rure block in console_state . 
 ruflo-mods 0.7.0: opt-in rureOffer (off by default, ADR-498) adds one line under an answer when the model touched a binary, library, .asar or CUDA file, saying ruRE can inspect it without running it. Offer only; the mods plugin is not part of the CLI tarball. 
 
 Fixed 
 
 Dependency audit: zod 4.6.7 in ruflo-graph-intelligence and @claude-flow/browser ( GHSA-mrhx-c7xc-m3w5 ). Nested zod 3 copies stay under two time-boxed accepted findings that expire 2026-11-23 ( #4442 , #4444 ).

</details>