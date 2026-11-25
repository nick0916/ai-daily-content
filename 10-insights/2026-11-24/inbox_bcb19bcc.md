---
id: inbox_bcb19bcc
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0006-infoq-main-qcon-san-francisco-2026-lessons-from-bui-c2ae]]"
title: "QCon San Francisco 2026: Lessons from Building a $100M Product in Six Weeks at OpenAI"
url: https://www.infoq.com/news/2026/11/qcon-sf-openai-lessons/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-24T06:32:00+00:00
fetched_at: 2026-11-25T00:12:48.721283+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 用 Codex agent、零人工手寫程式碼，六週做出一個廣告產品，工程師變成 agent 的管理者。 **Why** 當 agent 負責寫程式，瓶頸轉移到如何驗證與審查大量產出，並避免 agent 做出不安全的動作。 **How** 採分層測試、sandbox 隔離，以及批次化的 pull request review；並建議逐步導入。 **What** QCon SF 2026 上 OpenAI 的 Brian Yang 分享 ChatGPT ads 產品的開發經驗，標題為六週打造 $100M 產品。他點出的失敗模式包括程式碼「slop」與不安全的 agent 行為，並主張工程師應定位為 agent 的 manager。"
key_points:
  - "ChatGPT ads 產品用 Codex agents 開發，無人工手寫程式碼"
  - "分層測試、sandbox、批次 PR review 作為品質防線"
  - "失敗模式：程式碼 slop、agent 不安全動作；建議逐步導入並視工程師為 agent 管理者"
tags: [codex, agentic-coding, qcon, openai, code-review]
topics: [agents.coding_agents, product_and_org.adoption, foundation_models.gpt]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## QCon San Francisco 2026: Lessons from Building a $100M Product in Six Weeks at OpenAI

OpenAI 用 Codex agent、零人工手寫程式碼，六週做出一個廣告產品，工程師變成 agent 的管理者。

**Why** 當 agent 負責寫程式，瓶頸轉移到如何驗證與審查大量產出，並避免 agent 做出不安全的動作。

**How** 採分層測試、sandbox 隔離，以及批次化的 pull request review；並建議逐步導入。

**What** QCon SF 2026 上 OpenAI 的 Brian Yang 分享 ChatGPT ads 產品的開發經驗，標題為六週打造 $100M 產品。他點出的失敗模式包括程式碼「slop」與不安全的 agent 行為，並主張工程師應定位為 agent 的 manager。

### 重點
- ChatGPT ads 產品用 Codex agents 開發，無人工手寫程式碼
- 分層測試、sandbox、批次 PR review 作為品質防線
- 失敗模式：程式碼 slop、agent 不安全動作；建議逐步導入並視工程師為 agent 管理者

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/qcon-sf-openai-lessons/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

At QCon San Francisco 2026, OpenAI's Brian Yang described building the ChatGPT ads product with Codex agents and no human-written code. He outlined layered testing, sandboxes, and batched pull request reviews, and noted failure modes such as code "slop" and unsafe agent actions. He advised gradual adoption and framed engineers as managers of agents. By Daniel Curtis

</details>