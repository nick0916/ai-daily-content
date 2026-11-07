---
id: inbox_9aeb0161
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-infoq-main-article-identity-as-an-architectural-con-f764]]"
title: "Article: Identity as an Architectural Concern: Enterprise IAM Beyond Authentication"
url: https://www.infoq.com/articles/identity-as-architecture/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-06T09:00:00+00:00
fetched_at: 2026-11-07T01:46:05.649126+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "身分管理設計會決定資料模型、服務範圍與撤銷策略，應被視為架構問題而非事後補強。 **Why** 把 IAM 當附加功能，之後會被迫在資料模型與撤銷上妥協。 **How** 文章依服務帳號治理經驗，討論 graph 對比 RBAC、整合自己不擁有的 vault，以及為事件串流限定撤銷延遲。 **What** InfoQ 文章，作者 Vaishnavi Khosla，主張企業 IAM 超越認證，屬架構層級決策。"
key_points:
  - "身分設計決定資料模型、服務範圍與撤銷策略"
  - "比較 graph 與 RBAC 的取捨"
  - "討論整合非自有 vault，以及限定事件串流的撤銷延遲"
tags: [iam, identity, architecture, rbac, service-account]
topics: [security, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Identity as an Architectural Concern: Enterprise IAM Beyond Authentication

身分管理設計會決定資料模型、服務範圍與撤銷策略，應被視為架構問題而非事後補強。

**Why** 把 IAM 當附加功能，之後會被迫在資料模型與撤銷上妥協。

**How** 文章依服務帳號治理經驗，討論 graph 對比 RBAC、整合自己不擁有的 vault，以及為事件串流限定撤銷延遲。

**What** InfoQ 文章，作者 Vaishnavi Khosla，主張企業 IAM 超越認證，屬架構層級決策。

### 重點
- 身分設計決定資料模型、服務範圍與撤銷策略
- 比較 graph 與 RBAC 的取捨
- 討論整合非自有 vault，以及限定事件串流的撤銷延遲

**原文：** [infoq-main](https://www.infoq.com/articles/identity-as-architecture/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The way you design your identities will drive your data models, your service scope, and your revocation policies; enterprise identity management is thus an architectural problem, not an afterthought. Based on our experience in service account governance, this article touches upon graph vs. RBAC, integrating a vault you don't own, and bounding revocation latency for an event stream. By Vaishnavi Khosla

</details>