---
id: inbox_62fd74dc
date: 2026-10-31
source_ref: "[[00-inbox/2026-10-31/0019-infoq-main-google-discloses-pagebreak-ai-security-a-3f5d]]"
title: "Google Discloses PageBreak AI Security Agent That Found 500+ XSS Bugs"
url: https://www.infoq.com/news/2026/10/google-pagebreak-security-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-31T06:20:00+00:00
fetched_at: 2026-11-01T00:24:55.401989+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 去找漏洞，但只有程式能重現攻擊的才算數，藉此擋掉誤報。 **Why** AI 自主找漏洞容易回報看似合理、實際不成立的結果，需要一道確定性的把關。 **How** PageBreak 用 Gemini 模型自主調查潛在漏洞，只有當 deterministic validators 在運行中的應用上成功重現 exploit，才會提出報告。 **What** Google 論文揭露 AI 資安 agent PageBreak，自 1 月全面運作以來，在其 web 應用中找出 500 多個 XSS 漏洞。"
key_points:
  - "PageBreak 自 1 月進入全面運作，已在 Google web 應用中找出 500+ 個 XSS 漏洞"
  - "以 Gemini 模型自主調查潛在漏洞"
  - "報告前須由 deterministic validators 在運行中的應用上重現 exploit，才算有效發現"
tags: [google, pagebreak, xss, security-agent, gemini]
topics: [security, foundation_models.gemini]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Google Discloses PageBreak AI Security Agent That Found 500+ XSS Bugs

讓 AI 去找漏洞，但只有程式能重現攻擊的才算數，藉此擋掉誤報。

**Why** AI 自主找漏洞容易回報看似合理、實際不成立的結果，需要一道確定性的把關。

**How** PageBreak 用 Gemini 模型自主調查潛在漏洞，只有當 deterministic validators 在運行中的應用上成功重現 exploit，才會提出報告。

**What** Google 論文揭露 AI 資安 agent PageBreak，自 1 月全面運作以來，在其 web 應用中找出 500 多個 XSS 漏洞。

### 重點
- PageBreak 自 1 月進入全面運作，已在 Google web 應用中找出 500+ 個 XSS 漏洞
- 以 Gemini 模型自主調查潛在漏洞
- 報告前須由 deterministic validators 在運行中的應用上重現 exploit，才算有效發現

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/google-pagebreak-security-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

According to a paper published by Google, its AI-powered security agent has uncovered more than 500 XSS vulnerabilities across its web applications since entering full operation in January. PageBreak uses Gemini models to autonomously investigate potential vulnerabilities, but reports them only after deterministic validators successfully reproduce the exploit against a running application. By Renato Losio

</details>