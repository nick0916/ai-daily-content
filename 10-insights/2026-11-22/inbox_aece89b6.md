---
id: inbox_aece89b6
date: 2026-11-22
source_ref: "[[00-inbox/2026-11-22/0051-infoq-main-claude-code-has-been-leaking-secrets-thr-7d79]]"
title: "Claude Code Has Been Leaking Secrets through its \"Don't Ask Again\" Feature"
url: https://www.infoq.com/news/2026/11/claude-code-leaking-secrets/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-22T11:00:00+00:00
fetched_at: 2026-11-23T00:56:11.160680+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 為了實作「不再詢問」功能把內容存在本機檔案，結果有開發者把含機密的檔案推上公開 repo。 **Why** 本機設定檔一旦被提交到公開 repository，其中的機密就會外洩。 **How** 資安公司 Apiiro 指出，Claude Code 為實作「Don't Ask Again」，會把機密存進開發者機器上的本機檔案。 **What** Apiiro 在 claude/settings.local.json 檔案中找到 1,122 個 secrets，另在 git history、共用的 settings.json 以及存放在 repo 內的 agent 對話紀錄中找到 1,160 個。"
key_points:
  - "claude/settings.local.json 中發現 1,122 個 secrets"
  - "git history、共用 settings.json 與 repo 內 agent 對話紀錄另有 1,160 個"
  - "成因是 Claude Code 為「Don't Ask Again」將機密存於本機檔案"
tags: [claude-code, secrets-leak, apiiro, supply-chain-security, git-hygiene]
topics: [security, agents.coding_agents]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Code Has Been Leaking Secrets through its \"Don't Ask Again\" Feature

Claude Code 為了實作「不再詢問」功能把內容存在本機檔案，結果有開發者把含機密的檔案推上公開 repo。

**Why** 本機設定檔一旦被提交到公開 repository，其中的機密就會外洩。

**How** 資安公司 Apiiro 指出，Claude Code 為實作「Don't Ask Again」，會把機密存進開發者機器上的本機檔案。

**What** Apiiro 在 claude/settings.local.json 檔案中找到 1,122 個 secrets，另在 git history、共用的 settings.json 以及存放在 repo 內的 agent 對話紀錄中找到 1,160 個。

### 重點
- claude/settings.local.json 中發現 1,122 個 secrets
- git history、共用 settings.json 與 repo 內 agent 對話紀錄另有 1,160 個
- 成因是 Claude Code 為「Don't Ask Again」將機密存於本機檔案

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/claude-code-leaking-secrets/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Agentic security firm Apiiro found that Claude Code has been exposing secrets in public repositories due to how it stores them in local file on developers' machines to implement "Don't Ask Again". The company identified 1,122 secrets in claude/settings.local.json files and another 1,160 in git history, in the shared settings.json, and in agent chat transcripts stored in repos. By Sergio De Simone

</details>