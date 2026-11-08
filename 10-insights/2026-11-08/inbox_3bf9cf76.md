---
id: inbox_3bf9cf76
date: 2026-11-08
source_ref: "[[00-inbox/2026-11-08/2348-medium-tag-llm-i-let-claude-haiku-call-opus-when-it-was-1756]]"
title: "I Let Claude Haiku Call Opus When It Wasn’t Sure. It Called on the Clean Files"
url: https://medium.com/@lvyang860/i-let-claude-haiku-call-opus-when-it-wasnt-sure-it-called-on-the-clean-files-edabfb6b4ec3?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-08T23:31:46+00:00
fetched_at: 2026-11-08T23:54:01.190639+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓便宜的 Haiku 先處理，不確定時才升級給 Opus，以較低成本取得接近 Opus 的準確率。 **Why** 高階模型單價高，若每筆都交給它，成本難以負擔。 **How** 由 Haiku 先判斷，遇到不確定的案例才 escalate 給 Opus 處理。 **What** 原文稱 Hightouch 採用此做法，達到 Opus 級準確率、價格約為四分之一；作者表示親自測試，但截斷處未提供數據細節。"
key_points:
  - "Hightouch 讓 Haiku 先處理，只把不確定的案例升級給 Opus"
  - "原文宣稱達到 Opus 級準確率，價格約為四分之一"
  - "原文為 Medium 截斷摘要，評測方法與具體數據未提供"
tags: [model-cascade, cost-optimization, claude-haiku, claude-opus, escalation]
topics: [engineering.inference, foundation_models.claude]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## I Let Claude Haiku Call Opus When It Wasn’t Sure. It Called on the Clean Files

讓便宜的 Haiku 先處理，不確定時才升級給 Opus，以較低成本取得接近 Opus 的準確率。

**Why** 高階模型單價高，若每筆都交給它，成本難以負擔。

**How** 由 Haiku 先判斷，遇到不確定的案例才 escalate 給 Opus 處理。

**What** 原文稱 Hightouch 採用此做法，達到 Opus 級準確率、價格約為四分之一；作者表示親自測試，但截斷處未提供數據細節。

### 重點
- Hightouch 讓 Haiku 先處理，只把不確定的案例升級給 Opus
- 原文宣稱達到 Opus 級準確率，價格約為四分之一
- 原文為 Medium 截斷摘要，評測方法與具體數據未提供

**原文：** [medium-tag-llm](https://medium.com/@lvyang860/i-let-claude-haiku-call-opus-when-it-wasnt-sure-it-called-on-the-clean-files-edabfb6b4ec3?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hightouch got Opus-level accuracy for a quarter of the price by letting a cheap model escalate the cases it wasn’t sure about. I tried the... Continue reading on Medium »

</details>