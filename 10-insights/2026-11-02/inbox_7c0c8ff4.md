---
id: inbox_7c0c8ff4
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-infoq-main-shopify-overexposed-scans-gke-ingresses-38df]]"
title: "Shopify Overexposed Scans GKE Ingresses and Cloud Run for Exposure"
url: https://www.infoq.com/news/2026/11/shopify-kubernetes-ingresses/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-02T09:00:00+00:00
fetched_at: 2026-11-02T23:31:36.865334+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Shopify 自製掃描器，找出不小心暴露在公開網路、又沒有驗證的內部服務。 **What** Shopify 推出內部工具 Overexposed，用來找出 GKE 上的 Kubernetes Ingress 與 Cloud Run 服務中，可從網際網路存取且沒有身分驗證的項目。報導為 InfoQ 簡訊，作者 Claudio Masolo，原文摘要未提供掃描機制與成效數字。"
key_points:
  - "工具名稱為 Overexposed，屬 Shopify 內部使用的掃描器"
  - "掃描目標為 GKE 上的 Kubernetes Ingress 與 Cloud Run 服務"
  - "檢查條件是「可從網際網路存取且沒有驗證」"
tags: [shopify, kubernetes, gke, cloud-run, exposure-scanning]
topics: [security]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Shopify Overexposed Scans GKE Ingresses and Cloud Run for Exposure

Shopify 自製掃描器，找出不小心暴露在公開網路、又沒有驗證的內部服務。

**What** Shopify 推出內部工具 Overexposed，用來找出 GKE 上的 Kubernetes Ingress 與 Cloud Run 服務中，可從網際網路存取且沒有身分驗證的項目。報導為 InfoQ 簡訊，作者 Claudio Masolo，原文摘要未提供掃描機制與成效數字。

### 重點
- 工具名稱為 Overexposed，屬 Shopify 內部使用的掃描器
- 掃描目標為 GKE 上的 Kubernetes Ingress 與 Cloud Run 服務
- 檢查條件是「可從網際網路存取且沒有驗證」

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/shopify-kubernetes-ingresses/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Shopify has introduced Overexposed. This internal scanner locates Kubernetes Ingresses on GKE and Cloud Run services. It checks for those that are accessible from the internet without authentication By Claudio Masolo

</details>