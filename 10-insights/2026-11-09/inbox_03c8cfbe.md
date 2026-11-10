---
id: inbox_03c8cfbe
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2341-infoq-main-cloudflare-develops-public-certificate-a-4474]]"
title: "Cloudflare Develops Public Certificate Authority for Post-Quantum Web Security"
url: https://www.infoq.com/news/2026/11/cloudflare-merkle-certificates/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-09T14:35:00+00:00
fetched_at: 2026-11-10T00:04:08.386503+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用更精簡的憑證格式，讓網站在後量子加密時代不必多傳一大堆資料。 **Why** 後量子密碼學（post-quantum cryptography）會增加憑證的頻寬負擔。 **How** Cloudflare 開發公開憑證機構，簽發 Merkle Tree Certificates（MTCs）以降低頻寬開銷。 **What** Chrome 實驗中，Chrome Beta 146 的 50% 使用者在特定網域收到數十億份 MTC，回報中位數效能快 9%。要更廣泛部署，仍取決於瀏覽器支援、透明度與大規模正式環境驗證。"
key_points:
  - "Cloudflare 正開發支援 Merkle Tree Certificates（MTCs）的公開憑證機構"
  - "Chrome 實驗：Chrome Beta 146 的 50% 使用者、特定網域，數十億份 MTC，中位數效能快 9%"
  - "廣泛部署的前提：瀏覽器支援、透明度、正式規模驗證"
tags: [post-quantum, merkle-tree-certificates, cloudflare, certificate-authority, chrome]
topics: [security]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare Develops Public Certificate Authority for Post-Quantum Web Security

用更精簡的憑證格式，讓網站在後量子加密時代不必多傳一大堆資料。

**Why** 後量子密碼學（post-quantum cryptography）會增加憑證的頻寬負擔。

**How** Cloudflare 開發公開憑證機構，簽發 Merkle Tree Certificates（MTCs）以降低頻寬開銷。

**What** Chrome 實驗中，Chrome Beta 146 的 50% 使用者在特定網域收到數十億份 MTC，回報中位數效能快 9%。要更廣泛部署，仍取決於瀏覽器支援、透明度與大規模正式環境驗證。

### 重點
- Cloudflare 正開發支援 Merkle Tree Certificates（MTCs）的公開憑證機構
- Chrome 實驗：Chrome Beta 146 的 50% 使用者、特定網域，數十億份 MTC，中位數效能快 9%
- 廣泛部署的前提：瀏覽器支援、透明度、正式規模驗證

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/cloudflare-merkle-certificates/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare is developing a public certificate authority for Merkle Tree Certificates (MTCs) to reduce the bandwidth overhead of post-quantum cryptography. A Chrome experiment served billions of MTCs to 50% of Chrome Beta 146 for selected domains, reporting 9% faster median performance. Wider deployment depends on browser support, transparency, and production-scale validation. By Leela Kumili

</details>