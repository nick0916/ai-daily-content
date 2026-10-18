---
id: inbox_082b8f2d
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0256-infoq-architecture-presentation-how-to-find-resilience-bugs-e9c1]]"
title: "Presentation: How to Find Resilience Bugs in Systems that Don&#39;t Exist"
url: https://www.infoq.com/presentations/formal-methods-principles/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-10-14T11:00:00+00:00
fetched_at: 2026-10-18T03:15:04.844688+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "這是 InfoQ 上 Hillel Wayne 的演講，主題是如何運用形式化方法（formal methods）的原則，在系統尚未存在時就找出 resilience 與架構層級的 bug。依原文，他談到的原則包括 property strength、state-space verification 與 environment assumptions。他也分享實用的心智模型，例如「adversarial non-determinism」，用來推理並發、edge case 與分散式系統故障。重點是不需要複雜的數學工具即可應用。對架構師與後端工程師而言，可在設計階段就把『環境可能怎麼對我們作惡』當作檢查角度。原文摘要未提供更多範例或工具名稱，無法確定。"
key_points:
  - "形式化方法三原則：property strength、state-space verification、environment assumptions"
  - "心智模型「adversarial non-determinism」：用來推理並發、edge case 與分散式系統故障"
  - "不需複雜數學工具，可在系統尚未存在的設計階段找出架構 bug"
tags: [formal-methods, hillel-wayne, distributed-systems, resilience, design-review]
topics: [engineering.architecture]
importance: 2
novelty: 3
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: How to Find Resilience Bugs in Systems that Don't Exist

這是 InfoQ 上 Hillel Wayne 的演講，主題是如何運用形式化方法（formal methods）的原則，在系統尚未存在時就找出 resilience 與架構層級的 bug。依原文，他談到的原則包括 property strength、state-space verification 與 environment assumptions。他也分享實用的心智模型，例如「adversarial non-determinism」，用來推理並發、edge case 與分散式系統故障。重點是不需要複雜的數學工具即可應用。對架構師與後端工程師而言，可在設計階段就把『環境可能怎麼對我們作惡』當作檢查角度。原文摘要未提供更多範例或工具名稱，無法確定。

### 重點
- 形式化方法三原則：property strength、state-space verification、environment assumptions
- 心智模型「adversarial non-determinism」：用來推理並發、edge case 與分散式系統故障
- 不需複雜數學工具，可在系統尚未存在的設計階段找出架構 bug

**原文：** [infoq-architecture](https://www.infoq.com/presentations/formal-methods-principles/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hillel Wayne discusses how formal methods principles - such as property strength, state-space verification, and environment assumptions - help software engineers uncover critical architectural bugs early. He shares practical mental models like "adversarial non-determinism" to reason about concurrency, edge cases, and distributed system failures without needing complex mathematical tools. By Hillel Wayne

</details>