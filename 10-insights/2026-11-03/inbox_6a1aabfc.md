---
id: inbox_6a1aabfc
date: 2026-11-03
source_ref: "[[00-inbox/2026-11-03/2347-medium-tag-claude-i-measured-whether-my-claude-skills-help-24cd]]"
title: "I measured whether my Claude skills help. One of them made the code worse"
url: https://medium.com/@thisisfordeveloper/i-measured-whether-my-claude-skills-help-one-of-them-made-the-code-worse-358b6ba6182f?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-11-03T19:23:49+00:00
fetched_at: 2026-11-03T23:56:20.444426+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者實測 Claude skills 是否有效，發現其中一個讓程式碼變差。 **Why** 作者指出 SKILL.md 本質上是用英文寫的程式，而多數 skill 沒有測試。 **How** 作者以量測方式評估各個 skill 的效果。 **What** 實測結果顯示至少一個 skill 讓程式碼品質下降；摘要未給出樣本數或具體指標。"
key_points:
  - "SKILL.md 可視為由模型執行的英文程式，同樣可能有 bug"
  - "多數 skill 沒有測試，因此效果難以確認"
  - "實測中有一個 skill 讓程式碼變差；摘要未給指標數字"
tags: [claude-skills, evals, skill-testing, coding-agents]
topics: [agents.coding_agents, engineering.evals]
importance: 2
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I measured whether my Claude skills help. One of them made the code worse

作者實測 Claude skills 是否有效，發現其中一個讓程式碼變差。

**Why** 作者指出 SKILL.md 本質上是用英文寫的程式，而多數 skill 沒有測試。

**How** 作者以量測方式評估各個 skill 的效果。

**What** 實測結果顯示至少一個 skill 讓程式碼品質下降；摘要未給出樣本數或具體指標。

### 重點
- SKILL.md 可視為由模型執行的英文程式，同樣可能有 bug
- 多數 skill 沒有測試，因此效果難以確認
- 實測中有一個 skill 讓程式碼變差；摘要未給指標數字

**原文：** [medium-tag-claude](https://medium.com/@thisisfordeveloper/i-measured-whether-my-claude-skills-help-one-of-them-made-the-code-worse-358b6ba6182f?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A SKILL.md file is a program written in English. The model runs it, and like any program it can have bugs. Most skills have no tests, so... Continue reading on Medium »

</details>