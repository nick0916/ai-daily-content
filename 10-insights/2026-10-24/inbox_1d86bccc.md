---
id: inbox_1d86bccc
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0101-ruflo-releases-v3-62-0-rure-cuda-launch-plan-81de]]"
title: "v3.62.0 — ruRE CUDA launch plan"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.62.0
source: ruflo-releases
published_at: 2026-10-24T23:53:09+00:00
fetched_at: 2026-10-25T01:14:28.961569+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo 3.62.0 新增唯讀 MCP 工具，依 CUDA 架構規劃 kernel 的量測方案，且不執行程式。 **Why** 分析出的 CUDA kernel 需要量測計畫，才能判斷哪種資源（暫存器、shared memory 等）限制了每個 SM 上可同時執行的 blocks 與 warps。 **How** 以 sm_70 至 sm_120 共 8 種架構的表格計算 occupancy，未列出的架構不給數值；includeHarness 只回傳小型 CUDA 測試程式的文字。 **What** 新工具為 rure_cuda_launch_plan；occupancy 模型與 NVIDIA cuda_occupancy.h 在 1.77 million 組組合上一致，並與五張真實 GPU 的 CUDA driver 對照。另修正 standalone .cubin 被誤報為 sm_5 的問題，以及 daemon 設定優先序與 worker 取消流程。"
key_points:
  - "rure_cuda_launch_plan 為唯讀 MCP 工具，輸出每架構、每 kernel 在各 block size 下可容納的 blocks/warps 與限制資源"
  - "occupancy 模型與 cuda_occupancy.h 在 1.77 million 組組合上一致，並與五張真實 GPU 的 CUDA driver 對照"
  - "修正 CUDA 12 為 sm_70 至 sm_90 建置的 standalone .cubin 被誤報為 sm_5；maxConcurrent 等設定改為明確值優先 (#4462)"
tags: [ruflo, mcp, cuda, gpu-occupancy, rure]
topics: [agents.mcp, engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.62.0 — ruRE CUDA launch plan

ruflo 3.62.0 新增唯讀 MCP 工具，依 CUDA 架構規劃 kernel 的量測方案，且不執行程式。

**Why** 分析出的 CUDA kernel 需要量測計畫，才能判斷哪種資源（暫存器、shared memory 等）限制了每個 SM 上可同時執行的 blocks 與 warps。

**How** 以 sm_70 至 sm_120 共 8 種架構的表格計算 occupancy，未列出的架構不給數值；includeHarness 只回傳小型 CUDA 測試程式的文字。

**What** 新工具為 rure_cuda_launch_plan；occupancy 模型與 NVIDIA cuda_occupancy.h 在 1.77 million 組組合上一致，並與五張真實 GPU 的 CUDA driver 對照。另修正 standalone .cubin 被誤報為 sm_5 的問題，以及 daemon 設定優先序與 worker 取消流程。

### 重點
- rure_cuda_launch_plan 為唯讀 MCP 工具，輸出每架構、每 kernel 在各 block size 下可容納的 blocks/warps 與限制資源
- occupancy 模型與 cuda_occupancy.h 在 1.77 million 組組合上一致，並與五張真實 GPU 的 CUDA driver 對照
- 修正 CUDA 12 為 sm_70 至 sm_90 建置的 standalone .cubin 被誤報為 sm_5；maxConcurrent 等設定改為明確值優先 (#4462)

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.62.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Minor release: @claude-flow/cli , claude-flow , ruflo 3.62.0. Adds one MCP tool ( rure_cuda_launch_plan ). No leaf package changed, so no standalone publishes. 
 Added 
 
 ruRE: CUDA launch plan (ruflo-rure 0.6.0, ADR-501). New read-only MCP tool rure_cuda_launch_plan turns what rure_analyze_cuda found into a plan for measuring: per architecture and kernel, how many blocks and warps fit on one multiprocessor at each block size, which resource sets the limit (registers, shared memory, warps, block slots, barriers), the best block sizes and flags. Eight architectures have a table ( sm_70 to sm_120 ); any other gets no figure rather than a guess. It still parses and never runs: includeHarness only returns the text of a small CUDA program for you to build and run yourself. The occupancy model matches NVIDIA's cuda_occupancy.h on 1.77 million combinations and the CUDA driver on five real GPUs (ADR-501, ADR-500). 
 
 Fixed 
 
 rure_analyze_cuda reported the wrong architecture ( sm_5 ) for a standalone .cubin built with CUDA 12 for sm_70 to sm_90 ; the SM number sits in a different byte depending on the cubin's OS ABI. Cubins inside a fatbin or host binary were not affected. 
 The worker daemon let a maxConcurrent or workerTimeoutMs saved in daemon-state.json override the same setting in config.json ; an explicit value now wins (constructor, then config file, then saved state, then default) ( #4462 ). 
 Cancelling a headless worker now settles its execution and escalates to SIGKILL when the child ignores SIGTERM; the fallback timer no longer keeps the host alive, and a timed-out child no longer gets a second SIGTERM ( #4463 ). 
 
 Notes 
 
 Plugins in this tree that changed: ruflo-rure 0.6.0, ruflo-ai-team 0.3.4, ruflo-browser 0.3.7 (doctor path from other working directories), ruflo-x-gateway 0.10.2. The x.ruv.io gateway itself (0.9.1) is a separate deployment. 
 @claude-flow/swarm changes ( #4456 , #4457 ) are not a CLI dependency and are not part of this release.

</details>