---
id: inbox_bc08477f
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-infoq-main-presentation-move-fast-dont-break-trust-fe9c]]"
title: "Presentation: Move Fast, Don’t Break Trust: Shipping Constantly with Humans and Beyond"
url: https://www.infoq.com/presentations/monzo-microservices-devex/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-23T11:00:00+00:00
fetched_at: 2026-10-24T03:51:55.072857+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "靠強大的內部平台，讓工程師與 LLM 都能每天安全地大量上線。 **Why** 要在高頻發布的同時不犧牲可靠性與信任，這對金融業尤其關鍵。 **How** 以有主見的 microservice 抽象、基於 tenancy 的 staging、靜態分析檢查與持續 profiling，把安全護欄內建在平台中。 **What** Monzo 的 Suhail Patel 在 InfoQ 演講中分享其工程組織與技術堆疊，如何做到每天數百次安全部署，並讓人與 LLM 都能快速迭代。"
key_points:
  - "有主見的 microservice 抽象降低每個團隊的決策與出錯成本"
  - "Tenancy-based staging 搭配靜態分析檢查與持續 profiling 作為上線護欄"
  - "強內部平台讓工程師與 LLM 皆可快速迭代而不犧牲可靠性"
tags: [platform-engineering, microservices, monzo, developer-experience, continuous-deployment]
topics: [product_and_org.adoption, agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Move Fast, Don’t Break Trust: Shipping Constantly with Humans and Beyond

靠強大的內部平台，讓工程師與 LLM 都能每天安全地大量上線。 **Why** 要在高頻發布的同時不犧牲可靠性與信任，這對金融業尤其關鍵。 **How** 以有主見的 microservice 抽象、基於 tenancy 的 staging、靜態分析檢查與持續 profiling，把安全護欄內建在平台中。 **What** Monzo 的 Suhail Patel 在 InfoQ 演講中分享其工程組織與技術堆疊，如何做到每天數百次安全部署，並讓人與 LLM 都能快速迭代。

### 重點
- 有主見的 microservice 抽象降低每個團隊的決策與出錯成本
- Tenancy-based staging 搭配靜態分析檢查與持續 profiling 作為上線護欄
- 強內部平台讓工程師與 LLM 皆可快速迭代而不犧牲可靠性

**原文：** [infoq-main](https://www.infoq.com/presentations/monzo-microservices-devex/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Suhail Patel discusses how Monzo structures its software engineering organization and technical stack to ship safely hundreds of times a day. He shares insights into opinionated microservice abstractions, tenancy-based staging, static analysis checks, continuous profiling, demonstrating how a strong internal platform enables engineers and LLMs to iterate rapidly without sacrificing reliability. By Suhail Patel

</details>