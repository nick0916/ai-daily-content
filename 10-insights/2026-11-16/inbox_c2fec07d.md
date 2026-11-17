---
id: inbox_c2fec07d
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-infoq-main-aws-open-sources-emulator-for-local-test-ca96]]"
title: "AWS Open-Sources Emulator for Local Testing of 200+ Services by Coding Agents"
url: https://www.infoq.com/news/2026/11/aws-emulator-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-16T10:40:00+00:00
fetched_at: 2026-11-17T23:25:04.128079+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 開源本機模擬器，讓開發者與 coding agent 不用 AWS 帳號就能在本地測試 200 多項服務。 **Why** coding agent 需要反覆測試雲端程式碼，但每次都連真實 AWS 需要帳號、成本與權限設定。 **How** 依據公開的 Smithy API 模型自動產生本地 HTTPS endpoint，並公布各服務的擬真度（fidelity）分數。 **What** AWS Emulator 已 GA，支援逾 200 項 AWS 服務、無需帳號；文件載明 IAM、region 與 in-memory 狀態等限制。"
key_points:
  - "由公開 Smithy API 模型生成，涵蓋 200+ AWS 服務"
  - "本地 HTTPS endpoint，不需 AWS 帳號"
  - "公布各服務 fidelity 分數，並記載 IAM、region、in-memory 狀態的限制"
tags: [aws, emulator, coding-agents, local-testing, smithy]
topics: [agents.coding_agents, engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Open-Sources Emulator for Local Testing of 200+ Services by Coding Agents

AWS 開源本機模擬器，讓開發者與 coding agent 不用 AWS 帳號就能在本地測試 200 多項服務。

**Why** coding agent 需要反覆測試雲端程式碼，但每次都連真實 AWS 需要帳號、成本與權限設定。

**How** 依據公開的 Smithy API 模型自動產生本地 HTTPS endpoint，並公布各服務的擬真度（fidelity）分數。

**What** AWS Emulator 已 GA，支援逾 200 項 AWS 服務、無需帳號；文件載明 IAM、region 與 in-memory 狀態等限制。

### 重點
- 由公開 Smithy API 模型生成，涵蓋 200+ AWS 服務
- 本地 HTTPS endpoint，不需 AWS 帳號
- 公布各服務 fidelity 分數，並記載 IAM、region、in-memory 狀態的限制

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/aws-emulator-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS Emulator is a generally available local HTTPS endpoint, generated from public Smithy API models, that lets developers and coding agents test against more than 200 AWS services without an account, with published fidelity scores and documented limits around IAM, regions, and in-memory state. By Daniel Dominguez

</details>