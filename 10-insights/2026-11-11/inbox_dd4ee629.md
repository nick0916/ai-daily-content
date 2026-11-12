---
id: inbox_dd4ee629
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-simon-willison-llm-0-37-2-bbec]]"
title: "llm 0.37.2"
url: https://simonwillison.net/2026/Nov/11/llm/
source: simon-willison
published_at: 2026-11-11T17:19:52+00:00
fetched_at: 2026-11-12T02:58:27.300781+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修補 LLM 工具可能把 OpenAI API key 誤送給第三方供應商的安全問題。 **Why** LLM 透過 extra-openai-models.yaml（0.37 起由 llm openai endpoint add 管理）連接其他供應商的 OpenAI 相容端點，設定不當時金鑰可能外洩。 **How** Daniel de Araujo 回報兩種情境：api_key_name 指定的 key 從未儲存過，或以 -o chat_completions 1 執行 responses: true 的模型。 **What** llm 0.37.2 修復此問題，對應 GHSA-v9h7-jj4g-f862 與 GHSA-r639-rr7r-x72w。"
key_points:
  - "llm 0.37.2 修復兩個 GHSA 安全公告（GHSA-v9h7-jj4g-f862、GHSA-r639-rr7r-x72w）"
  - "觸發情境一：api_key_name 指定的 key 從未儲存"
  - "觸發情境二：responses: true 的模型搭配 -o chat_completions 1 執行"
tags: [llm-cli, security, api-key-leak, openai-compatible, release]
topics: [security]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.37.2

修補 LLM 工具可能把 OpenAI API key 誤送給第三方供應商的安全問題。

**Why** LLM 透過 extra-openai-models.yaml（0.37 起由 llm openai endpoint add 管理）連接其他供應商的 OpenAI 相容端點，設定不當時金鑰可能外洩。

**How** Daniel de Araujo 回報兩種情境：api_key_name 指定的 key 從未儲存過，或以 -o chat_completions 1 執行 responses: true 的模型。

**What** llm 0.37.2 修復此問題，對應 GHSA-v9h7-jj4g-f862 與 GHSA-r639-rr7r-x72w。

### 重點
- llm 0.37.2 修復兩個 GHSA 安全公告（GHSA-v9h7-jj4g-f862、GHSA-r639-rr7r-x72w）
- 觸發情境一：api_key_name 指定的 key 從未儲存
- 觸發情境二：responses: true 的模型搭配 -o chat_completions 1 執行

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/11/llm/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm 0.37.2 
 Fixes a security issue reported by Daniel de Araujo in GHSA-v9h7-jj4g-f862 and GHSA-r639-rr7r-x72w . 
 LLM has a mechanism called extra-openai-models.yaml - now managed by the new-in-0.37 llm openai endpoint add command - for using LLM with OpenAI-compatible API endpoints from other providers. 
 Daniel reported two ways this could accidentally send your configured OpenAI API key to one of those providers: if the key named by api_key_name had never been stored, or if a responses: true model was run with -o chat_completions 1 . 
 
 
 Tags: projects , security , llm , releases

</details>