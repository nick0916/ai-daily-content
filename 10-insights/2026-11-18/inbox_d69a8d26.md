---
id: inbox_d69a8d26
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-infoq-main-aws-privatelink-tunnel-endpoints-open-a-07b7]]"
title: "AWS PrivateLink Tunnel Endpoints Open a Whole CIDR Range to Another Account"
url: https://www.infoq.com/news/2026/11/aws-privatelink-tunnel-endpoints/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-18T09:29:00+00:00
fetched_at: 2026-11-19T08:18:32.249792+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 的 PrivateLink 新增一種端點，讓一個帳號的 VPC 能一次連到另一帳號的整段網段，而不是一次只連一個資源。 **Why** 原本 PrivateLink 一次只能暴露單一資源，遇到整個網段、位址空間重疊的情境不好處理。 **How** 使用 tunnel endpoints，消費端以 GENEVE 封裝流量，且只能由消費端發起連線。 **What** 支援重疊位址空間；限制是僅 TCP 與 DNS 可通過，且 access log 無法歸屬到端點後面的具體 workload。"
key_points:
  - "Tunnel endpoints 讓消費端 VPC 存取另一帳號的整段 CIDR 網段"
  - "消費端須以 GENEVE 封裝流量，且僅能由消費端發起連線"
  - "僅支援 TCP 與 DNS，access log 無法歸因到後端 workload"
tags: [aws, privatelink, vpc, networking, geneve]
topics: [engineering.architecture, security]
importance: 2
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS PrivateLink Tunnel Endpoints Open a Whole CIDR Range to Another Account

AWS 的 PrivateLink 新增一種端點，讓一個帳號的 VPC 能一次連到另一帳號的整段網段，而不是一次只連一個資源。

**Why** 原本 PrivateLink 一次只能暴露單一資源，遇到整個網段、位址空間重疊的情境不好處理。

**How** 使用 tunnel endpoints，消費端以 GENEVE 封裝流量，且只能由消費端發起連線。

**What** 支援重疊位址空間；限制是僅 TCP 與 DNS 可通過，且 access log 無法歸屬到端點後面的具體 workload。

### 重點
- Tunnel endpoints 讓消費端 VPC 存取另一帳號的整段 CIDR 網段
- 消費端須以 GENEVE 封裝流量，且僅能由消費端發起連線
- 僅支援 TCP 與 DNS，access log 無法歸因到後端 workload

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/aws-privatelink-tunnel-endpoints/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS has detailed tunnel endpoints, a PrivateLink endpoint type that gives a consumer VPC access to an entire network segment in another account rather than one resource at a time, over an overlapping address space and with consumer-initiated connections only. The consumer must wrap traffic in GENEVE; only TCP and DNS pass, and access logs cannot attribute traffic to a workload behind the endpoint. By Steef-Jan Wiggers

</details>