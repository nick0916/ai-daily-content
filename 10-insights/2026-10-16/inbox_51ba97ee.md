---
id: inbox_51ba97ee
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0102-lobsters-vibecoding-do-you-let-llms-write-both-your-tests-an-a352]]"
title: "Do you let LLMs write both your tests and your code?"
url: https://lobste.rs/s/miwcai/do_you_let_llms_write_both_your_tests_your
source: lobsters-vibecoding
published_at: 2026-10-16T18:53:05-05:00
fetched_at: 2026-10-25T01:28:03.600760+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "LLM 同時寫程式與測試，可能產生只驗證自己的同義反覆測試。 **Why** 作者審 MR 時發現測試高度同義反覆，且程式似為了寫更多測試而過度設計。 **How** 作者提議在 values.md 加入規則：LLM 只能主要生成測試或程式其中一項。 **What** 這是一則徵詢他人經驗的提問貼文，文中未提供量化數據或結論。"
key_points:
  - "作者觀察到一份 MR 中，LLM 同時產出程式與測試，測試被描述為高度同義反覆"
  - "作者認為程式可能因為要產生更多測試而被過度設計"
  - "提議規則：values.md 中要求 LLM 只能主要生成測試或程式其中一項"
tags: [llm-testing, tautological-tests, code-review, coding-agents]
topics: [engineering.evals, agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Do you let LLMs write both your tests and your code?

LLM 同時寫程式與測試，可能產生只驗證自己的同義反覆測試。 **Why** 作者審 MR 時發現測試高度同義反覆，且程式似為了寫更多測試而過度設計。 **How** 作者提議在 values.md 加入規則：LLM 只能主要生成測試或程式其中一項。 **What** 這是一則徵詢他人經驗的提問貼文，文中未提供量化數據或結論。

### 重點
- 作者觀察到一份 MR 中，LLM 同時產出程式與測試，測試被描述為高度同義反覆
- 作者認為程式可能因為要產生更多測試而被過度設計
- 提議規則：values.md 中要求 LLM 只能主要生成測試或程式其中一項

**原文：** [lobsters-vibecoding](https://lobste.rs/s/miwcai/do_you_let_llms_write_both_your_tests_your)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I'm curious what stance others have taken? Or what they've experienced with this? I'm toying with adding a rule to our values.md that the LLM can only significantly generate one or the other. 
 I'm reviewing a merge request at the moment where it's clear the LLM mostly did both, and they're highly tautological. And I can see how it over engineered the code, just to be able to write more tests almost.

</details>