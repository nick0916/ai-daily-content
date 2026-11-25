---
id: inbox_8c926f4f
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0008-hackernews-ask-hn-anthropic-is-accusing-my-company-1117]]"
title: "Ask HN: Anthropic is accusing my company of distilling. How can I prove I'm not?"
url: https://news.ycombinator.com/item?id=50630809
source: hackernews
published_at: 2026-11-24T16:45:44+00:00
fetched_at: 2026-11-25T00:12:48.722282+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "有公司被 Anthropic 指控用 API 做模型蒸餾，必須在 24 小時內自證清白。 **Why** 該公司說自己不訓練模型，只在調整 AI 設定時跑自動化回歸 benchmark，卻可能因此被判定為蒸餾，又不能為舉證而洩漏使用者隱私。 **What** 這是一則 Ask HN 求助貼文：發文者稱 Anthropic 指控其公司蒸餾，給了 24 小時證明，詢問有無人遇過、如何在不侵犯使用者隱私下自證。貼文僅為單方說法，Anthropic 的認定依據與結果原文沒有提供。"
key_points:
  - "發文者稱 Anthropic 指控其公司以 API 蒸餾，要求 24 小時內舉證"
  - "公司自述不訓練自有模型，唯一可疑用量是設定變更時的自動化回歸 benchmark"
  - "核心難題：如何在不洩漏使用者隱私的前提下證明未蒸餾"
tags: [distillation, anthropic-api, usage-policy, regression-benchmark, ask-hn]
topics: [foundation_models.claude, security, engineering.evals]
importance: 2
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Ask HN: Anthropic is accusing my company of distilling. How can I prove I'm not?

有公司被 Anthropic 指控用 API 做模型蒸餾，必須在 24 小時內自證清白。

**Why** 該公司說自己不訓練模型，只在調整 AI 設定時跑自動化回歸 benchmark，卻可能因此被判定為蒸餾，又不能為舉證而洩漏使用者隱私。

**What** 這是一則 Ask HN 求助貼文：發文者稱 Anthropic 指控其公司蒸餾，給了 24 小時證明，詢問有無人遇過、如何在不侵犯使用者隱私下自證。貼文僅為單方說法，Anthropic 的認定依據與結果原文沒有提供。

### 重點
- 發文者稱 Anthropic 指控其公司以 API 蒸餾，要求 24 小時內舉證
- 公司自述不訓練自有模型，唯一可疑用量是設定變更時的自動化回歸 benchmark
- 核心難題：如何在不洩漏使用者隱私的前提下證明未蒸餾

**原文：** [hackernews](https://news.ycombinator.com/item?id=50630809)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Basically the title. Anthropic is accusing me and my company of using their API for distillation. We are not. We do not train our own models. Our only usage which I think could get us flagged is automated regression benchmarks whenever we change some AI settings. But this is not against their policy? Now I've got 24h to prove we didn't. Has anyone dealt with this too? How can you prove that you are not distilling Anthropic models without breaking your user's privacy?

</details>