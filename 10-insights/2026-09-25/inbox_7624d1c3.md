---
id: inbox_7624d1c3
date: 2026-09-25
source_ref: "[[00-inbox/2026-09-25/0256-superpowers-releases-v6-4-2-4fe9]]"
title: "v6.4.2"
url: https://github.com/obra/superpowers/releases/tag/v6.4.2
source: superpowers-releases
published_at: 2026-09-25T18:08:09+00:00
fetched_at: 2026-10-18T03:22:01.933103+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Superpowers v6.4.2 改寫 writing-plans skill，讓計畫更精簡、產出更快。新版計畫只記錄實作者需要的決策（函式簽名、測試斷言、spec 中的數值），而不是把完整程式碼寫出來。原文指出部分前沿模型（包含 Opus 5.5）在特定提示下會過度積極，在規劃階段就試圖實作整個專案；新 skill 讓規劃聚焦於計畫本身。重現原始回報後，scratch build 消失，計畫耗時降為約四分之一、token 約為三分之一（感謝 Harper Reed 提供回報與 session bundle，#2333）。具體改動包括：以「What a Step Contains」取代「No Placeholders」章節；測試步驟需列出測試名與斷言，程式碼步驟給出簽名、檔案與 spec 數值，只有在這些無法決定的演算法才附函式本體；self-review 會比較計畫與 spec 的長度，計畫長度若為 spec 數倍就視為「逐字稿」；讀者設定改為「有能力的工程師」，步驟大小定義為「一個有可檢查結果的動作」。新 skill 產出的計畫在 Sonnet 5 上對植入缺陷的探針執行 9/9，與完整程式碼計畫相同。另外移除未被引用的 plan-document-reviewer-prompt.md，並刪除 CLAUDE.md，因為 Claude Code 只在沒有 CLAUDE.md 時才直接讀 AGENTS.md。"
key_points:
  - "計畫改記錄決策（簽名、測試斷言、spec 數值）而非完整程式碼：耗時約 1/4、token 約 1/3，且 scratch build 消失（#2333）"
  - "self-review 比較計畫與 spec 長度，數倍於 spec 即視為逐字稿；程式碼區塊過多時改為簽名加測試斷言"
  - "在 Sonnet 5 上對植入缺陷探針執行 9/9，與完整程式碼計畫結果相同；並移除 CLAUDE.md 讓 Claude Code 直接讀 AGENTS.md"
tags: [superpowers, writing-plans, plan-mode, token-efficiency, agents-md]
topics: [agents.coding_agents, engineering.evals, foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v6.4.2

Superpowers v6.4.2 改寫 writing-plans skill，讓計畫更精簡、產出更快。新版計畫只記錄實作者需要的決策（函式簽名、測試斷言、spec 中的數值），而不是把完整程式碼寫出來。原文指出部分前沿模型（包含 Opus 5.5）在特定提示下會過度積極，在規劃階段就試圖實作整個專案；新 skill 讓規劃聚焦於計畫本身。重現原始回報後，scratch build 消失，計畫耗時降為約四分之一、token 約為三分之一（感謝 Harper Reed 提供回報與 session bundle，#2333）。具體改動包括：以「What a Step Contains」取代「No Placeholders」章節；測試步驟需列出測試名與斷言，程式碼步驟給出簽名、檔案與 spec 數值，只有在這些無法決定的演算法才附函式本體；self-review 會比較計畫與 spec 的長度，計畫長度若為 spec 數倍就視為「逐字稿」；讀者設定改為「有能力的工程師」，步驟大小定義為「一個有可檢查結果的動作」。新 skill 產出的計畫在 Sonnet 5 上對植入缺陷的探針執行 9/9，與完整程式碼計畫相同。另外移除未被引用的 plan-document-reviewer-prompt.md，並刪除 CLAUDE.md，因為 Claude Code 只在沒有 CLAUDE.md 時才直接讀 AGENTS.md。

### 重點
- 計畫改記錄決策（簽名、測試斷言、spec 數值）而非完整程式碼：耗時約 1/4、token 約 1/3，且 scratch build 消失（#2333）
- self-review 比較計畫與 spec 長度，數倍於 spec 即視為逐字稿；程式碼區塊過多時改為簽名加測試斷言
- 在 Sonnet 5 上對植入缺陷探針執行 9/9，與完整程式碼計畫結果相同；並移除 CLAUDE.md 讓 Claude Code 直接讀 AGENTS.md

**原文：** [superpowers-releases](https://github.com/obra/superpowers/releases/tag/v6.4.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

writing-plans produces leaner plans, faster. Plans now record the decisions an implementer needs (signatures, test assertions, the spec's values) instead of writing out the code. Some frontier models, including Opus 5.5, could get overzealous during plan writing and, with certain prompting, would sometimes try to implement the entire project while designing the plan. The new skill keeps planning focused on the plan. When we reproduced the original report, the scratch builds went away, and plans took a quarter of the time and about a third of the tokens. Thanks to Harper Reed for the report and session bundle. ( #2333 ) 
 Writing Plans 
 
 A plan records decisions. It's not a transcript of the code. "What a Step Contains" replaces the "No Placeholders" section. A test step names the test and its assertions. A code step gives the exact signature, the file, and the spec's values, and includes a body only for an algorithm those don't determine. A verification step gives the command and its passing output. A reference to another task goes through that task's Interfaces block. Placeholders are still called out as the opposite failure. ( #2333 ) 
 Self-review checks proportion. The plan compares its own length to the spec's. A plan several times longer than the spec is a transcript, and when code blocks dominate, bodies get replaced with signatures and test assertions. ( #2333 ) 
 The plan's reader is described as capable: an engineer who writes idiomatic code once they know the exact interface and test. This replaces "zero context, questionable taste." Steps are now sized as "one action with a checkable result" instead of "2-5 minutes." ( #2333 ) 
 Every plan written by the new skill executed 9/9 against planted-defect probes on Sonnet 5, the same result as full-code plans. ( #2333 ) 
 Removed plan-document-reviewer-prompt.md . Nothing referenced it. ( #2333 ) 
 
 Documentation 
 
 Removed CLAUDE.md . Claude Code now reads AGENTS.md directly, but only when no CLAUDE.md exists, so keeping the one-line pointer would have hidden the real guidelines.

</details>