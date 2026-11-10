---
id: inbox_2ef9d90c
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2323-infoq-main-google-finds-that-technical-debt-can-der-2daf]]"
title: "Google Finds that Technical Debt Can Derail Coding Agents Through \"Agent Distraction\""
url: https://www.infoq.com/news/2026/11/google-agent-distraction/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-10T18:00:00+00:00
fetched_at: 2026-11-10T23:29:52.451704+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "過時的程式碼註解與舊規格會把 AI coding agent 帶偏，讓它去做沒人要求的事。 **Why** Google 工程師 Sam Saccone 與 Madhuri Garikapati 指出，技術債不只拖累人，也會干擾 agent。 **What** 他們稱此現象為「agent distraction」：agent 被陳舊的 TODO 註解、過時的 bug 參照與失效規格吸引，展開未被要求的「side-quests」。原文摘要未提供量化數據。"
key_points:
  - "Google 提出「agent distraction」概念：技術債會讓 coding agent 偏離任務"
  - "誘因包括舊 TODO 註解、過時 bug 參照、失效 spec，導致 agent 去做未被要求的 side-quest"
  - "實務含意：清理陳舊註解與文件可能也是提升 agent 可靠度的手段（此為依摘要的推論，非原文明述）"
tags: [agent-distraction, technical-debt, coding-agents, google, context-hygiene]
topics: [agents.coding_agents]
importance: 3
novelty: 4
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Google Finds that Technical Debt Can Derail Coding Agents Through \"Agent Distraction\"

過時的程式碼註解與舊規格會把 AI coding agent 帶偏，讓它去做沒人要求的事。

**Why** Google 工程師 Sam Saccone 與 Madhuri Garikapati 指出，技術債不只拖累人，也會干擾 agent。

**What** 他們稱此現象為「agent distraction」：agent 被陳舊的 TODO 註解、過時的 bug 參照與失效規格吸引，展開未被要求的「side-quests」。原文摘要未提供量化數據。

### 重點
- Google 提出「agent distraction」概念：技術債會讓 coding agent 偏離任務
- 誘因包括舊 TODO 註解、過時 bug 參照、失效 spec，導致 agent 去做未被要求的 side-quest
- 實務含意：清理陳舊註解與文件可能也是提升 agent 可靠度的手段（此為依摘要的推論，非原文明述）

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/google-agent-distraction/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In a recent article, Google senior staff software engineer Sam Saccone and senior staff data scientist Madhuri Garikapati highlighted the cost of agent distraction, where AI coding agents get derailed by stale technical debt, such as old TODO comments, obsolete bug references, and outdated specs, leading them to embark on unrequested "side-quests". By Sergio De Simone

</details>