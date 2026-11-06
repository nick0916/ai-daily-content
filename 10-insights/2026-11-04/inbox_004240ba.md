---
id: inbox_004240ba
date: 2026-11-04
source_ref: "[[00-inbox/2026-11-04/0002-infoq-main-amazon-ecs-gateway-arrives-with-generate-3070]]"
title: "Amazon ECS Gateway Arrives with Generated Hostnames and No Custom Domain Support"
url: https://www.infoq.com/news/2026/11/introducing-amazon-ecs-gateway/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-04T09:49:00+00:00
fetched_at: 2026-11-06T00:09:18.330818+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 讓平台團隊一次定義 ECS 網路入口，應用團隊再選擇加入。 **What** AWS 推出 Amazon ECS Gateway，為帳號層級的 ingress 資源，應用團隊透過 connector 讓服務加入；每個服務獲得系統產生的 hostname，採 host-based routing，公告與文件均未提及自訂網域支援。"
key_points:
  - "帳號層級 ingress 資源：平台團隊定義一次網路，應用團隊用 connector opt-in"
  - "每個服務取得生成的 hostname，路由為 host-based"
  - "公告與文件皆未涵蓋自訂網域"
tags: [aws, amazon-ecs, ecs-gateway, ingress, platform-engineering]
topics: [product_and_org.product]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Amazon ECS Gateway Arrives with Generated Hostnames and No Custom Domain Support

AWS 讓平台團隊一次定義 ECS 網路入口，應用團隊再選擇加入。

**What** AWS 推出 Amazon ECS Gateway，為帳號層級的 ingress 資源，應用團隊透過 connector 讓服務加入；每個服務獲得系統產生的 hostname，採 host-based routing，公告與文件均未提及自訂網域支援。

### 重點
- 帳號層級 ingress 資源：平台團隊定義一次網路，應用團隊用 connector opt-in
- 每個服務取得生成的 hostname，路由為 host-based
- 公告與文件皆未涵蓋自訂網域

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/introducing-amazon-ecs-gateway/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS has released Amazon ECS Gateway, an account-level ingress resource letting platform teams define networking once and application teams opt services in with a connector. Each service gets a generated hostname and routing is host-based, and neither the announcement nor the documentation covers custom domains. By Steef-Jan Wiggers

</details>