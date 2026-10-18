---
id: inbox_37d9fe9a
date: 2026-10-13
source_ref: "[[00-inbox/2026-10-13/0256-simon-willison-quoting-geoffrey-huntley-8df7]]"
title: "Quoting Geoffrey Huntley"
url: https://simonwillison.net/2026/Oct/13/geoffrey-huntley/
source: simon-willison
published_at: 2026-10-13T13:32:00+00:00
fetched_at: 2026-10-18T03:04:53.000433+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 引述 Geoffrey Huntley 文章（「nobody should type code by hand anymore. here's what's left.」）的一段話，討論如何讓 coding agent 穩定遵守專案慣例。Huntley 指出，若 agent 沒有使用他的 diagnostics library，即使反覆檢視並更新 AGENTS.md，指示與實際行為之間仍有落差且會隨時間 drift。他的做法是改寫一個 pre-commit hook，檢查 git diff 中是否有繞過 diagnostics 模組、直接呼叫 observability 模組的程式碼；若有就讓 commit 失敗，並注入 prompt 要求 agent 改用 diagnostics library。依他的說法，這樣之後遵守率就變成「十次中有十次」。實務意義是：靠文件（AGENTS.md）提示屬於機率性約束，靠 hook 在流程中強制檢查並回饋給 agent 才是確定性約束。"
key_points:
  - "問題：僅靠更新 AGENTS.md 要求 agent 使用 diagnostics library，仍有落差且會 drift"
  - "做法：pre-commit hook 檢查 git diff 是否直接呼叫 observability 模組而繞過 diagnostics 模組，違規即 fail commit 並注入 prompt 指示 agent 改用 diagnostics library"
  - "結果（作者自述）：agent 遵守率變成十次中有十次"
tags: [coding-agents, pre-commit-hook, agents-md, guardrails, agentic-engineering]
topics: [agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Geoffrey Huntley

Simon Willison 引述 Geoffrey Huntley 文章（「nobody should type code by hand anymore. here's what's left.」）的一段話，討論如何讓 coding agent 穩定遵守專案慣例。Huntley 指出，若 agent 沒有使用他的 diagnostics library，即使反覆檢視並更新 AGENTS.md，指示與實際行為之間仍有落差且會隨時間 drift。他的做法是改寫一個 pre-commit hook，檢查 git diff 中是否有繞過 diagnostics 模組、直接呼叫 observability 模組的程式碼；若有就讓 commit 失敗，並注入 prompt 要求 agent 改用 diagnostics library。依他的說法，這樣之後遵守率就變成「十次中有十次」。實務意義是：靠文件（AGENTS.md）提示屬於機率性約束，靠 hook 在流程中強制檢查並回饋給 agent 才是確定性約束。

### 重點
- 問題：僅靠更新 AGENTS.md 要求 agent 使用 diagnostics library，仍有落差且會 drift
- 做法：pre-commit hook 檢查 git diff 是否直接呼叫 observability 模組而繞過 diagnostics 模組，違規即 fail commit 並注入 prompt 指示 agent 改用 diagnostics library
- 結果（作者自述）：agent 遵守率變成十次中有十次

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/13/geoffrey-huntley/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

If the agent isn't using my diagnostics library, I could introspect and update AGENTS.md, but there's still a delta, and it'll drift. Instead, I write a pre-commit hook that checks the git diff for direct calls to observability modules that bypass my diagnostics module. Boom: fail the commit, inject a prompt telling the agent to use the diagnostics library. All of a sudden it's ten out of ten. 
 &mdash; Geoffrey Huntley , nobody should type code by hand anymore. here's what's left. 

 Tags: coding-agents , generative-ai , git , agentic-engineering , ai , geoffrey-huntley , llms

</details>