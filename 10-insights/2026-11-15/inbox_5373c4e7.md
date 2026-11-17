---
id: inbox_5373c4e7
date: 2026-11-15
source_ref: "[[00-inbox/2026-11-15/2317-infoq-architecture-cloudflare-introduces-private-origins-fo-3983]]"
title: "Cloudflare Introduces Private Origins for Application Services"
url: https://www.infoq.com/news/2026/11/cloudflare-private-origins/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design
source: infoq-architecture
published_at: 2026-11-15T06:18:00+00:00
fetched_at: 2026-11-17T23:25:44.355236+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓公開流量能連到私有網路裡的應用，又不必把應用的 IP 暴露出去。 **What** Cloudflare 宣布 Application Services for Private Origins 正式 GA，公開流量可到達架設在私有網路的應用，不需暴露其 IP 位址，也不必開放入站防火牆連接埠。目前尚不支援 private-to-private 連線。"
key_points:
  - "Cloudflare Application Services for Private Origins 正式 GA"
  - "無需暴露來源 IP，也不需開放入站防火牆連接埠"
  - "尚未支援 private-to-private 連線"
tags: [cloudflare, private-origins, network-security, infoq]
topics: [engineering.architecture, security]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Introduces Private Origins for Application Services

讓公開流量能連到私有網路裡的應用，又不必把應用的 IP 暴露出去。

**What** Cloudflare 宣布 Application Services for Private Origins 正式 GA，公開流量可到達架設在私有網路的應用，不需暴露其 IP 位址，也不必開放入站防火牆連接埠。目前尚不支援 private-to-private 連線。

### 重點
- Cloudflare Application Services for Private Origins 正式 GA
- 無需暴露來源 IP，也不需開放入站防火牆連接埠
- 尚未支援 private-to-private 連線

**原文：** [infoq-architecture](https://www.infoq.com/news/2026/11/cloudflare-private-origins/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=Architecture+%26+Design)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare recently made Application Services for Private Origins generally available, allowing public traffic to reach applications hosted on private networks without exposing their IP addresses or opening inbound firewall ports. Private-to-private connectivity is not yet supported. By Renato Losio

</details>