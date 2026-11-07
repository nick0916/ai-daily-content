---
id: inbox_19b5da3e
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-infoq-main-vault-fork-openbao-adds-external-keys-an-f513]]"
title: "Vault Fork OpenBao Adds External Keys and Quantum-Ready TLS"
url: https://www.infoq.com/news/2026/11/vault-fork-openbao-27/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-06T09:00:00+00:00
fetched_at: 2026-11-07T01:46:35.444825+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Vault 的開源分支 OpenBao 發布 2.7，新增外部金鑰、後量子加密與敏感操作的人工審核。 **What** OpenBao 2.7 為 PostgreSQL 後端部署加入讀取擴展，支援外部 HSM 與 KMS 金鑰，並加入後量子密碼演算法。另新增 control groups，讓敏感操作需經人工審核；也新增 header，讓請求在負載平衡的多個 OpenBao 節點間保持一致。"
key_points:
  - "OpenBao 2.7 為 PostgreSQL 後端部署加入讀取擴展（read scaling）"
  - "支援外部 HSM 與 KMS 金鑰，並加入後量子密碼演算法"
  - "新增 control groups 供人工審核敏感操作，並新增 header 維持負載平衡節點間的請求一致性"
tags: [openbao, vault-fork, secrets-management, post-quantum, hsm-kms]
topics: [security]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Vault Fork OpenBao Adds External Keys and Quantum-Ready TLS

Vault 的開源分支 OpenBao 發布 2.7，新增外部金鑰、後量子加密與敏感操作的人工審核。

**What** OpenBao 2.7 為 PostgreSQL 後端部署加入讀取擴展，支援外部 HSM 與 KMS 金鑰，並加入後量子密碼演算法。另新增 control groups，讓敏感操作需經人工審核；也新增 header，讓請求在負載平衡的多個 OpenBao 節點間保持一致。

### 重點
- OpenBao 2.7 為 PostgreSQL 後端部署加入讀取擴展（read scaling）
- 支援外部 HSM 與 KMS 金鑰，並加入後量子密碼演算法
- 新增 control groups 供人工審核敏感操作，並新增 header 維持負載平衡節點間的請求一致性

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/vault-fork-openbao-27/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

OpenBao has released version 2.7, adding read scaling for PostgreSQL-backed deployments, support for external hardware security module (HSM) and key management service (KMS) keys, and post-quantum cryptographic algorithms. The release also introduces control groups for human review of sensitive operations and new headers intended to keep requests consistent across load-balanced OpenBao nodes. By Matt Saunders

</details>