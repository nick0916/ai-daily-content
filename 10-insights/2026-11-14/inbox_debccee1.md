---
id: inbox_debccee1
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0124-medium-tag-llm-stop-prompting-coding-agents-with-resume-5e11]]"
title: "Stop Prompting Coding Agents With Resumes (192-Run Benchmark)"
url: https://medium.com/@zachariah.abraham.abby1/stop-prompting-coding-agents-with-resumes-192-run-benchmark-4f503fe40023?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-14T19:16:10+00:00
fetched_at: 2026-11-15T01:30:41.293665+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "給 coding agent 套上資深工程師或名校博士的身分描述，並沒有幫助。 **Why** 角色式（履歷式）提示是常見做法，需要實測其效果。 **How** 以 192 次執行的基準測試比較不同提示寫法。 **What** 「Expert SWE」提示比空白提示更差，「Google / MIT PhD」人設只是模仿資歷；只有明確寫出的不變量（invariants）會改變資料結構。"
key_points:
  - "192 次基準測試：「Expert SWE」提示比空白提示更差"
  - "「Google / MIT PhD」人設只是模仿資歷，未改善結果"
  - "只有明確寫出的不變量（invariants）會改變 agent 的資料結構設計"
tags: [prompt-engineering, coding-agents, benchmark, persona-prompting]
topics: [agents.coding_agents, engineering.evals]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop Prompting Coding Agents With Resumes (192-Run Benchmark)

給 coding agent 套上資深工程師或名校博士的身分描述，並沒有幫助。

**Why** 角色式（履歷式）提示是常見做法，需要實測其效果。

**How** 以 192 次執行的基準測試比較不同提示寫法。

**What** 「Expert SWE」提示比空白提示更差，「Google / MIT PhD」人設只是模仿資歷；只有明確寫出的不變量（invariants）會改變資料結構。

### 重點
- 192 次基準測試：「Expert SWE」提示比空白提示更差
- 「Google / MIT PhD」人設只是模仿資歷，未改善結果
- 只有明確寫出的不變量（invariants）會改變 agent 的資料結構設計

**原文：** [medium-tag-llm](https://medium.com/@zachariah.abraham.abby1/stop-prompting-coding-agents-with-resumes-192-run-benchmark-4f503fe40023?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

"Expert SWE" was worse than an empty prompt. "Google / MIT PhD" cosplayed seniority. Only explicit invariants changed data structures. Continue reading on Medium »

</details>