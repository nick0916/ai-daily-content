---
id: inbox_e3be425a
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2342-hackernews-chatgpt-desktop-forwards-your-ssh-agent-485d]]"
title: "ChatGPT Desktop forwards your SSH agent to remote machines"
url: https://news.ycombinator.com/item?id=50422628
source: hackernews
published_at: 2026-11-09T08:17:49+00:00
fetched_at: 2026-11-10T00:04:44.630345+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ChatGPT Desktop 會把你本機的 SSH agent 轉發給遠端機器，遠端的 agent 因此能用你的本機 SSH 憑證。 **Why** 遠端機器上執行的 agent 取得了本機身分驗證能力，是潛在的憑證暴露風險。 **What** 貼文指出遠端 agent 可用本機 SSH 憑證驗證，例如推送到你在 GitHub 上的私有 repo；佐證連結為 openai/codex 的 PR 討論（#28131）。"
key_points:
  - "ChatGPT Desktop 會將本機 SSH agent 轉發到遠端機器"
  - "遠端 agent 能以本機 SSH 憑證驗證，例如推送到 GitHub 私有 repo"
  - "證據為 openai/codex PR #28131 的討論串"
tags: [ssh-agent-forwarding, chatgpt-desktop, credential-exposure, openai-codex, agent-security]
topics: [security, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## ChatGPT Desktop forwards your SSH agent to remote machines

ChatGPT Desktop 會把你本機的 SSH agent 轉發給遠端機器，遠端的 agent 因此能用你的本機 SSH 憑證。

**Why** 遠端機器上執行的 agent 取得了本機身分驗證能力，是潛在的憑證暴露風險。

**What** 貼文指出遠端 agent 可用本機 SSH 憑證驗證，例如推送到你在 GitHub 上的私有 repo；佐證連結為 openai/codex 的 PR 討論（#28131）。

### 重點
- ChatGPT Desktop 會將本機 SSH agent 轉發到遠端機器
- 遠端 agent 能以本機 SSH 憑證驗證，例如推送到 GitHub 私有 repo
- 證據為 openai/codex PR #28131 的討論串

**原文：** [hackernews](https://news.ycombinator.com/item?id=50422628)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The agent running on a remote machine can authenticate using your local SSH credentials. That means it can push to your private repos on GitHub, for example. Proof: https://github.com/openai/codex/pull/28131#discussion_r3410013180

</details>