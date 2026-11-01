---
id: inbox_2034f10a
date: 2026-10-31
source_ref: "[[00-inbox/2026-10-31/0019-infoq-main-cloudflares-post-quantum-geokey-manager-e1ae]]"
title: "Cloudflare’s Post-Quantum GeoKey Manager Enters Closed Beta Without Attribute-Based Encryption"
url: https://www.infoq.com/news/2026/10/cf-pq-geokey-manager/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-31T19:56:00+00:00
fetched_at: 2026-11-01T00:24:26.312652+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 把限定地區的金鑰管理系統改成抗量子加密，金鑰只存在驗證過的區域伺服器記憶體中。 **Why** 要讓地理限制的金鑰在量子運算時代仍然安全，同時取代 2022 年起使用的屬性式加密。 **How** 以 ML-KEM-768 與 X25519 的混合加密保護金鑰；金鑰只存在已驗證區域伺服器的 kernel 記憶體，任何驗證失敗都會直接拒絕請求（fail-closed）。 **What** Cloudflare 的 post-quantum GeoKey Manager 進入 closed beta，預計 2027 年第 1 季 GA。實務人員擔心 fail-closed 設計可能造成區域性服務中斷。"
key_points:
  - "以 ML-KEM-768 + X25519 混合加密取代 2022 年起使用的屬性式加密（ABE）"
  - "金鑰僅存於已驗證區域伺服器的 kernel 記憶體，驗證失敗即拒絕請求"
  - "closed beta 中，GA 預計 2027 Q1；fail-closed 可能引發區域中斷疑慮"
tags: [post-quantum, cloudflare, geokey-manager, ml-kem, key-management]
topics: [security]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Cloudflare’s Post-Quantum GeoKey Manager Enters Closed Beta Without Attribute-Based Encryption

Cloudflare 把限定地區的金鑰管理系統改成抗量子加密，金鑰只存在驗證過的區域伺服器記憶體中。

**Why** 要讓地理限制的金鑰在量子運算時代仍然安全，同時取代 2022 年起使用的屬性式加密。

**How** 以 ML-KEM-768 與 X25519 的混合加密保護金鑰；金鑰只存在已驗證區域伺服器的 kernel 記憶體，任何驗證失敗都會直接拒絕請求（fail-closed）。

**What** Cloudflare 的 post-quantum GeoKey Manager 進入 closed beta，預計 2027 年第 1 季 GA。實務人員擔心 fail-closed 設計可能造成區域性服務中斷。

### 重點
- 以 ML-KEM-768 + X25519 混合加密取代 2022 年起使用的屬性式加密（ABE）
- 金鑰僅存於已驗證區域伺服器的 kernel 記憶體，驗證失敗即拒絕請求
- closed beta 中，GA 預計 2027 Q1；fail-closed 可能引發區域中斷疑慮

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/cf-pq-geokey-manager/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cloudflare has moved a post-quantum rebuild of GeoKey Manager into closed beta, guarding geo-fenced keys with hybrid ML-KEM-768 and X25519 instead of the attribute-based encryption used since 2022. Keys live only in kernel memory on verified regional servers, and any failed check rejects the request, a fail-closed choice practitioners ask could cause a regional outage. GA is planned for Q1 2027. By Steef-Jan Wiggers

</details>