---
id: inbox_0b9993a1
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-gitnexus-releases-rc-e6ae04ed84284b74c5aba7de3e3adf79aed1c-581f]]"
title: "rc/e6ae04ed84284b74c5aba7de3e3adf79aed1ce43: fix(embeddings): reject corrupt identities before mutation (#3614)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fe6ae04ed84284b74c5aba7de3e3adf79aed1ce43
source: gitnexus-releases
published_at: 2026-10-17T17:45:28+00:00
fetched_at: 2026-10-18T03:18:46.227319+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus rc 標籤 rc/e6ae04ed… 收錄 PR #3614「fix(embeddings): reject corrupt identities before mutation」，屬 U2 工作單元。主要變更包括：在變更（mutation）之前拒絕損毀的 embedding identity、保留精確的 Unicode key、在開啟 CSV 前先驗證 identity、在變更前驗證 cache。CI 方面新增 native embedding identity benchmark 閘門，並讓 identity 證明測試在原生 OS 上執行；文件也補上 CSV identity 驗證流程說明。共同作者為 Gergo Magyar。實務意義是 embedding 儲存層採「先驗證、後寫入」，避免損毀資料污染既有索引；但原文未提供 benchmark 數字或影響版本。"
key_points:
  - "PR #3614（U2）：embedding identity 損毀時於 mutation 前拒絕，並驗證 cache 後才變更"
  - "保留精確 Unicode key，且在開啟 CSV 前先驗證 identity"
  - "CI 新增 native embedding identity benchmark 閘門，identity 測試改在原生 OS 執行"
tags: [gitnexus, embeddings, validation, unicode, ci]
topics: [engineering.rag]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/e6ae04ed84284b74c5aba7de3e3adf79aed1ce43: fix(embeddings): reject corrupt identities before mutation (#3614)

GitNexus rc 標籤 rc/e6ae04ed… 收錄 PR #3614「fix(embeddings): reject corrupt identities before mutation」，屬 U2 工作單元。主要變更包括：在變更（mutation）之前拒絕損毀的 embedding identity、保留精確的 Unicode key、在開啟 CSV 前先驗證 identity、在變更前驗證 cache。CI 方面新增 native embedding identity benchmark 閘門，並讓 identity 證明測試在原生 OS 上執行；文件也補上 CSV identity 驗證流程說明。共同作者為 Gergo Magyar。實務意義是 embedding 儲存層採「先驗證、後寫入」，避免損毀資料污染既有索引；但原文未提供 benchmark 數字或影響版本。

### 重點
- PR #3614（U2）：embedding identity 損毀時於 mutation 前拒絕，並驗證 cache 後才變更
- 保留精確 Unicode key，且在開啟 CSV 前先驗證 identity
- CI 新增 native embedding identity benchmark 閘門，identity 測試改在原生 OS 執行

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fe6ae04ed84284b74c5aba7de3e3adf79aed1ce43)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(embeddings): reject corrupt identities before mutation (U2) 
 
 
 fix(embeddings): preserve exact Unicode keys (U2) 
 
 
 fix(storage): validate identities before opening CSVs 
 
 
 fix(embeddings): validate caches before mutation 
 
 
 ci: gate native embedding identity benchmark 
 
 
 test(embeddings): run identity proofs on native OSes 
 
 
 docs: describe CSV identity validation pass 
 
 
 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com

</details>