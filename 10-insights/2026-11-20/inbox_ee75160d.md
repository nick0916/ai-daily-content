---
id: inbox_ee75160d
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0047-infoq-main-aws-releases-a-free-local-emulator-of-aw-2110]]"
title: "AWS Releases a Free Local Emulator of AWS Built Entirely by Agents"
url: https://www.infoq.com/news/2026/11/aws-emulator-local-testing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-20T06:53:00+00:00
fetched_at: 2026-11-21T00:53:21.648380+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS 推出免費的本機版 AWS 模擬器，專供 coding agent 在測試迴圈中使用，而且程式碼全由 agent 撰寫與維護。 **Why** coding agent 需要在本機快速、低成本地反覆測試雲端服務呼叫。 **How** 從 AWS 公開的 API 模型自動生成 200 多項服務的替身，並於每次發布公開逐版本的擬真度（fidelity）分數。 **What** AWS Emulator 採 CC0 授權、免費；AWS 表示所有程式碼皆由 agent 撰寫維護。文件指出它不評估 IAM，實務工作者對於信任一個沒人審查過的模擬器看法分歧。"
key_points:
  - "AWS Emulator：免費、CC0 授權，模擬超過 200 項 AWS 服務"
  - "由公開 API 模型生成，所有程式碼由 agent 撰寫與維護，每次發布公開擬真度分數"
  - "文件說明不評估 IAM；社群對未經人工審查的模擬器是否可信意見分歧"
tags: [aws, aws-emulator, coding-agents, local-testing, cc0]
topics: [agents.coding_agents, engineering.evals]
importance: 4
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Releases a Free Local Emulator of AWS Built Entirely by Agents

AWS 推出免費的本機版 AWS 模擬器，專供 coding agent 在測試迴圈中使用，而且程式碼全由 agent 撰寫與維護。

**Why** coding agent 需要在本機快速、低成本地反覆測試雲端服務呼叫。

**How** 從 AWS 公開的 API 模型自動生成 200 多項服務的替身，並於每次發布公開逐版本的擬真度（fidelity）分數。

**What** AWS Emulator 採 CC0 授權、免費；AWS 表示所有程式碼皆由 agent 撰寫維護。文件指出它不評估 IAM，實務工作者對於信任一個沒人審查過的模擬器看法分歧。

### 重點
- AWS Emulator：免費、CC0 授權，模擬超過 200 項 AWS 服務
- 由公開 API 模型生成，所有程式碼由 agent 撰寫與維護，每次發布公開擬真度分數
- 文件說明不評估 IAM；社群對未經人工審查的模擬器是否可信意見分歧

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/aws-emulator-local-testing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS has released AWS Emulator, a free, CC0-licensed local stand-in for more than 200 of its services, generated from its public API models and aimed at the test loops of coding agents. AWS says agents wrote and maintain all of the code and publishes per-release fidelity scores. The docs say it does not evaluate IAM, and practitioners are split on trusting an emulator nobody reviewed. By Steef-Jan Wiggers

</details>