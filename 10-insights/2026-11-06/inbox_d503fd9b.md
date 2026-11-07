---
id: inbox_d503fd9b
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0140-infoq-main-edera-s-object-capability-bounded-author-d323]]"
title: "Edera's Object Capability Bounded Authority Promises to Isolate Credentials From AI Agent Workloads"
url: https://www.infoq.com/news/2026/11/ai-credentials-isolation/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-06T06:06:00+00:00
fetched_at: 2026-11-07T01:46:35.447551+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 AI agent 需要的權限與背後的憑證分開，讓 agent 身上不必存放密碼。 **How** 以 hypervisor 強制執行的 capability，將 agent 限制在特定動作內，且不在 workload 中儲存 secret。 **What** Edera 發表 Object Capability Bounded Authority 安全模型，適用於 AI agent 與 MCP server。首批涵蓋範圍限定的指令執行與 workload identity，憑證代理式（credential-brokered）API 存取之後推出。"
key_points:
  - "Edera 發表 Object Capability Bounded Authority，將 agent/MCP server 所需權限與其背後憑證分離"
  - "由 hypervisor 強制執行 capability，workload 內不存放 secret"
  - "首批支援 scoped command execution 與 workload identity，credential-brokered API access 後續推出"
tags: [edera, ai-agent-security, mcp, capability-security, credential-isolation]
topics: [security, agents.mcp]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Edera's Object Capability Bounded Authority Promises to Isolate Credentials From AI Agent Workloads

把 AI agent 需要的權限與背後的憑證分開，讓 agent 身上不必存放密碼。

**How** 以 hypervisor 強制執行的 capability，將 agent 限制在特定動作內，且不在 workload 中儲存 secret。

**What** Edera 發表 Object Capability Bounded Authority 安全模型，適用於 AI agent 與 MCP server。首批涵蓋範圍限定的指令執行與 workload identity，憑證代理式（credential-brokered）API 存取之後推出。

### 重點
- Edera 發表 Object Capability Bounded Authority，將 agent/MCP server 所需權限與其背後憑證分離
- 由 hypervisor 強制執行 capability，workload 內不存放 secret
- 首批支援 scoped command execution 與 workload identity，credential-brokered API access 後續推出

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/ai-credentials-isolation/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Edera announced Object Capability Bounded Authority, a security model that separates an AI agent's or MCP server's required authority from the credentials behind it. Hypervisor-enforced capabilities limit agents to specific actions without storing secrets in the workload. Initial releases cover scoped command execution and workload identity; credential-brokered API access will follow. By Olimpiu Pop

</details>