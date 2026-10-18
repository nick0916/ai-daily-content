---
id: inbox_3e98db66
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-medium-tag-llm-a-successful-import-is-not-a-correct-one-f9ff]]"
title: "A Successful Import Is Not a Correct One"
url: https://medium.com/@wiqi_lee/a-successful-import-is-not-a-correct-one-2135d6c107ec?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-17T18:21:59+00:00
fetched_at: 2026-10-18T03:17:13.157339+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者介紹自己打造的 MoveProof，核心設計是讓 AI 只負責提出計畫，由確定性（deterministic）程式碼執行已核准的變更，再由獨立檢查驗證暫存（staged）資料。標題「成功匯入不等於正確匯入」點出論點：流程跑完沒報錯，不代表資料正確，因此需要獨立驗證。內文在此截斷，具體使用的模型、驗證規則與錯誤攔截數據無法確定。對做資料匯入或 agent 自動化的人而言，可借鏡的原則是把「提案、執行、驗證」拆成不同角色，不讓 LLM 直接改動資料。

```mermaid
flowchart LR
  A[AI 提出計畫] --> B[人工/規則核准]
  B --> C[確定性程式碼執行]
  C --> D[暫存資料 staged]
  D --> E[獨立檢查驗證]
```"
key_points:
  - "分工：AI 提案、確定性程式碼執行已核准變更、獨立檢查驗證 staged 資料"
  - "論點：匯入成功不等於資料正確，需獨立驗證"
  - "專案名稱 MoveProof；驗證細節與成效數據在提供內容中缺失"
tags: [moveproof, deterministic-execution, verification, data-import, ai-safety-pattern]
topics: [agents.frameworks, engineering.evals]
importance: 2
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## A Successful Import Is Not a Correct One

作者介紹自己打造的 MoveProof，核心設計是讓 AI 只負責提出計畫，由確定性（deterministic）程式碼執行已核准的變更，再由獨立檢查驗證暫存（staged）資料。標題「成功匯入不等於正確匯入」點出論點：流程跑完沒報錯，不代表資料正確，因此需要獨立驗證。內文在此截斷，具體使用的模型、驗證規則與錯誤攔截數據無法確定。對做資料匯入或 agent 自動化的人而言，可借鏡的原則是把「提案、執行、驗證」拆成不同角色，不讓 LLM 直接改動資料。

```mermaid
flowchart LR
  A[AI 提出計畫] --> B[人工/規則核准]
  B --> C[確定性程式碼執行]
  C --> D[暫存資料 staged]
  D --> E[獨立檢查驗證]
```

### 重點
- 分工：AI 提案、確定性程式碼執行已核准變更、獨立檢查驗證 staged 資料
- 論點：匯入成功不等於資料正確，需獨立驗證
- 專案名稱 MoveProof；驗證細節與成效數據在提供內容中缺失

**原文：** [medium-tag-llm](https://medium.com/@wiqi_lee/a-successful-import-is-not-a-correct-one-2135d6c107ec?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How I built MoveProof: AI proposes plans, deterministic code executes approved changes, and independent checks verify staged data before&#x2026; Continue reading on Medium »

</details>