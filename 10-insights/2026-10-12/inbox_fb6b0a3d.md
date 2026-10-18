---
id: inbox_fb6b0a3d
date: 2026-10-12
source_ref: "[[00-inbox/2026-10-12/0256-ruflo-releases-v3-56-8-shared-3-0-4-pinned-coverage-gap-2263]]"
title: "v3.56.8 — shared 3.0.4 pinned, coverage-gaps fixes, TUI page bar"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.56.8
source: ruflo-releases
published_at: 2026-10-12T17:40:51+00:00
fetched_at: 2026-10-18T03:20:23.508534+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 發布 v3.56.8 patch（@claude-flow/cli、claude-flow、ruflo），CLI 現在 pin 住 @claude-flow/shared 3.0.4（3.56.7 仍 pin 3.0.3），其他已發布套件與 signed helpers 均無變更。shared 3.0.4 讓 RVF event log 在附加寫入前先修復不完整或損毀的尾端（#4031）；乾淨安裝後可正常 import `.`、`./core`、`./mcp`，因為 zod 與 express 現已正確宣告為依賴，且 tarball 不再附帶編譯後的測試檔（#4089、#4091）。此 fresh-consumer 問題由 @martinvlad 發現，並新增 scripts/smoke-shared-fresh-consumer.mjs 涵蓋。`hooks coverage-gaps` 修正：沒有可執行行的檔案不再被報為 0%、整體覆蓋率改為依行數加權、指令改讀 coverage-final.json，並限制報告大小（#4082–#4084、#4097）；ruflo-testgen 與 ruflo-sparc 的 plugin workflow contract 同步更正。`ruflo tui` 在以 `--view ai` 啟動時，page bar 會標示 AI 頁（6 AI），說明文字改為 pages 1-6，且 policy-trust 路徑不再相對於工作目錄解析（#4105、#4106）。README 與文件新增 ruflo tui 動畫導覽（#4103）。對實務的意義：使用 shared 套件的消費端不再遇到缺依賴的 import 失敗，覆蓋率報告也更可信。"
key_points:
  - "shared 3.0.4 宣告 zod 與 express 依賴，修復 clean install 時 `.`、`./core`、`./mcp` 無法 import 的問題，並移除 tarball 內編譯後測試檔"
  - "hooks coverage-gaps：無可執行行的檔案不再算 0%，整體覆蓋率改為行數加權，改讀 coverage-final.json"
  - "RVF event log 在 append 前先修復損毀或不完整的尾端（#4031）"
tags: [ruflo, coverage-gaps, tui, packaging-fix, rvf-event-log]
topics: [agents.coding_agents, engineering.evals]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.56.8 — shared 3.0.4 pinned, coverage-gaps fixes, TUI page bar

Ruflo 發布 v3.56.8 patch（@claude-flow/cli、claude-flow、ruflo），CLI 現在 pin 住 @claude-flow/shared 3.0.4（3.56.7 仍 pin 3.0.3），其他已發布套件與 signed helpers 均無變更。shared 3.0.4 讓 RVF event log 在附加寫入前先修復不完整或損毀的尾端（#4031）；乾淨安裝後可正常 import `.`、`./core`、`./mcp`，因為 zod 與 express 現已正確宣告為依賴，且 tarball 不再附帶編譯後的測試檔（#4089、#4091）。此 fresh-consumer 問題由 @martinvlad 發現，並新增 scripts/smoke-shared-fresh-consumer.mjs 涵蓋。`hooks coverage-gaps` 修正：沒有可執行行的檔案不再被報為 0%、整體覆蓋率改為依行數加權、指令改讀 coverage-final.json，並限制報告大小（#4082–#4084、#4097）；ruflo-testgen 與 ruflo-sparc 的 plugin workflow contract 同步更正。`ruflo tui` 在以 `--view ai` 啟動時，page bar 會標示 AI 頁（6 AI），說明文字改為 pages 1-6，且 policy-trust 路徑不再相對於工作目錄解析（#4105、#4106）。README 與文件新增 ruflo tui 動畫導覽（#4103）。對實務的意義：使用 shared 套件的消費端不再遇到缺依賴的 import 失敗，覆蓋率報告也更可信。

### 重點
- shared 3.0.4 宣告 zod 與 express 依賴，修復 clean install 時 `.`、`./core`、`./mcp` 無法 import 的問題，並移除 tarball 內編譯後測試檔
- hooks coverage-gaps：無可執行行的檔案不再算 0%，整體覆蓋率改為行數加權，改讀 coverage-final.json
- RVF event log 在 append 前先修復損毀或不完整的尾端（#4031）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.56.8)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.8 (latest, alpha, v3alpha). The CLI now pins @claude-flow/shared 3.0.4 (3.56.7 still pinned 3.0.3). No other published package changed since 3.56.7; signed helpers did not change. 
 Fixed 
 
 @claude-flow/shared 3.0.4 : the RVF event log repairs an incomplete or damaged tail before appending ( #4031 , @rudycelekli ). A clean install can import . , ./core and ./mcp because zod and express are now declared, and the tarball no longer ships compiled tests ( #4089 , #4091 , @proffesor-for-testing ). The fresh-consumer finding behind this came from @martinvlad , and scripts/smoke-shared-fresh-consumer.mjs now covers it. 
 hooks coverage-gaps : files with no executable lines are no longer reported as 0%, overall coverage is line-weighted, the command reads coverage-final.json , and report size is capped ( #4082 - #4084 reported by @ronmikailov ; #4097 ). Plugin workflow contracts for ruflo-testgen and ruflo-sparc were corrected in the same change ( #4085 - #4088 ; marketplace plugins, not npm). 
 ruflo tui : the page bar marks the AI page (6 AI) when started with --view ai , and the help text says pages 1-6 ( #4105 , #4106 ). The policy-trust path is never resolved relative to the working directory ( #4106 ). 
 The README and docs now cover ruflo tui with the animated walkthrough ( #4103 ). 
 
 Thanks 
 @rudycelekli , @proffesor-for-testing , @martinvlad , @ronmikailov and @Devesh-Maheshwari for the reports and fixes that shaped 3.56.6 through 3.56.8.

</details>