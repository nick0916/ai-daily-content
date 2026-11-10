---
id: inbox_ccd2b39d
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2324-hackernews-show-hn-get-your-coding-agent-off-2019-j-74cc]]"
title: "Show HN: Get your coding agent off ~2019 JavaScript, onto modern web primitives"
url: https://github.com/GoogleChrome/modern-web-guidance
source: hackernews
published_at: 2026-11-10T18:01:15+00:00
fetched_at: 2026-11-10T23:30:20.300706+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "給 coding agent 一份最新的網頁標準做法指南，讓它別再寫 2019 年風格的 JavaScript。 **Why** 模型知道不少原生 API 的名稱，卻仍習慣預設用舊的 JS 加套件寫法，而不是瀏覽器原生方案。 **How** 以 agent skill 搭配 CLI 提供 200+ 份手工撰寫的指南（約 1.7MB），用 Agentic RAG 檢索：從 500MB 原生堆疊縮到約 7MB 純 JS，CPU 上搜尋約 10ms；另有以 3 萬個 GitHub repo 訓練的確定性 legacy-scan 找出舊寫法。 **What** Chrome 團隊與 Firefox、MDN、Edge 合作釋出 modern-web-guidance 1.0（開源）。在 200 個任務、約 1,700 個 Playwright / AST 斷言下，用 codex / claude / agy 測試，通過率由 55% 升到 92%；legacy-scan 在保留測試 repo 上平均精準度 92%。"
key_points:
  - "評測：200 個任務、約 1,700 個斷言，agent 通過率 55%（無指南）→ 92%（有指南）"
  - "RAG 瘦身：500MB 原生堆疊 → 約 7MB 純 JS，CPU 搜尋約 10ms；legacy-scan 平均精準度 92%"
  - "安裝：npx modern-web-guidance@latest install，並有 search、legacy-scan 指令"
tags: [agent-skill, chrome, web-standards, agentic-rag, coding-agent]
topics: [agents.coding_agents, engineering.rag, engineering.evals]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Get your coding agent off ~2019 JavaScript, onto modern web primitives

給 coding agent 一份最新的網頁標準做法指南，讓它別再寫 2019 年風格的 JavaScript。

**Why** 模型知道不少原生 API 的名稱，卻仍習慣預設用舊的 JS 加套件寫法，而不是瀏覽器原生方案。

**How** 以 agent skill 搭配 CLI 提供 200+ 份手工撰寫的指南（約 1.7MB），用 Agentic RAG 檢索：從 500MB 原生堆疊縮到約 7MB 純 JS，CPU 上搜尋約 10ms；另有以 3 萬個 GitHub repo 訓練的確定性 legacy-scan 找出舊寫法。

**What** Chrome 團隊與 Firefox、MDN、Edge 合作釋出 modern-web-guidance 1.0（開源）。在 200 個任務、約 1,700 個 Playwright / AST 斷言下，用 codex / claude / agy 測試，通過率由 55% 升到 92%；legacy-scan 在保留測試 repo 上平均精準度 92%。

### 重點
- 評測：200 個任務、約 1,700 個斷言，agent 通過率 55%（無指南）→ 92%（有指南）
- RAG 瘦身：500MB 原生堆疊 → 約 7MB 純 JS，CPU 搜尋約 10ms；legacy-scan 平均精準度 92%
- 安裝：npx modern-web-guidance@latest install，並有 search、legacy-scan 指令

**原文：** [hackernews](https://github.com/GoogleChrome/modern-web-guidance)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Browsers natively handle a lot of what used to take 50 lines of JS (or a dependency): `CSS.highlights` for text range highlighting without s everywhere, ` ` and showModal() give you backdrops and ideal focus management, `field-sizing` to auto-grow textareas as the user types.. (Something yesterday's ftrain post touched on [0]) Models know about some of these by name, but consistently won't default to using the platform-native solution and instead prefer the incumbent +JS based pattern. We started an effort in Chrome to supplement coding agents with this key domain knowledge and we're shipping our 1.0 today, in collaboration with Firefox, MDN, and Edge. 200+ guides (~1.7MB) of curated, hand-crafted implementation best-practices from web experts, updated as the web evolves. (Open source, obv, so.. we'll welcome your bikeshedding ;) Readable versions here: [1] I've spent the last 9 months obsessing over how to ship this as an agent skill + (Agentic RAG) CLI without blowing up your context window. (Or cedeing activation mechanics to MCP dynamic tool search). The skill description is minmaxed for activating on relevant frontend tasks. The RAG work I'm pretty proud of... originally a 500mb native stack down to a ~7MB pure-JS package, ~10ms search on your CPU. We just introduced a deterministic 'legacy-scan' (trained on 30k github repos) to identify old 'n dusted patterns that your agent can modernize. (92% avg precision on held-out repos.) People make a lot of claims about what coding agents are good/bad at. We wanted receipts, so we invested heavily in eval infra [2] to help us hill-climb, but also to identify when knowledge is common enough we can prune our guides. (Ofc, some of the things we thought AI didn't know turned out to be wrong :) We run codex/claude/agy against 200 tasks without the skill and then with.. In total ~1,700 playwright/AST-based assertions. Agents go from 55% pass unguided to 92% guided. Try it out: DISABLE_TELEMETRY=1 npx modern-web-guidance@latest install
 DISABLE_TELEMETRY=1 npx modern-web-guidance@latest search "animate dialog modal"
 DISABLE_TELEMETRY=1 npx modern-web-guidance@latest legacy-scan ./src
 
If you spot something wrong or weird, give us a holler! Longer write-up on the 1.0: https://developer.chrome.com/blog/modern-web-guidance-v1 --- 0: https://news.ycombinator.com/item?id=50416456 1: https://developer.chrome.com/docs/modern-web-guidance/guides 2: https://googlechrome.github.io/modern-web-guidance-src/

</details>