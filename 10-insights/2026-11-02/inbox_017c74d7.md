---
id: inbox_017c74d7
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-infoq-main-uber-builds-mcp-gateway-to-govern-access-b84f]]"
title: "Uber Builds MCP Gateway to Govern Access to 800+ Servers and 5,000+ AI Agent Tools"
url: https://www.infoq.com/news/2026/11/uber-mcp-gateway-ai-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-02T13:53:00+00:00
fetched_at: 2026-11-02T23:30:59.141776+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 建了一個閘道，統一管理 AI agent 能找到、能呼叫哪些內部服務。 **Why** 內部有大量 MCP server 與工具，需要集中治理存取與敏感資料。 **How** 把工具註冊與執行期呼叫分開，並提供自動 API 探索、存取控制、敏感資料遮蔽、透過 Omni MCP 的漸進式工具探索，以及回應過濾。 **What** Uber MCP Gateway 涵蓋 800+ 個 MCP server 與 5,000+ 個工具，供 AI agent 標準化地發現並呼叫內部服務。"
key_points:
  - "規模：800+ MCP server、5,000+ 工具，由單一 MCP Gateway 治理"
  - "設計：工具註冊與執行期呼叫分離，並有自動 API 探索與存取控制"
  - "防護與效率：敏感資料遮蔽、回應過濾，以及透過 Omni MCP 做漸進式工具探索"
tags: [mcp, uber, mcp-gateway, ai-agents, access-control]
topics: [agents.mcp, security]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber Builds MCP Gateway to Govern Access to 800+ Servers and 5,000+ AI Agent Tools

Uber 建了一個閘道，統一管理 AI agent 能找到、能呼叫哪些內部服務。

**Why** 內部有大量 MCP server 與工具，需要集中治理存取與敏感資料。

**How** 把工具註冊與執行期呼叫分開，並提供自動 API 探索、存取控制、敏感資料遮蔽、透過 Omni MCP 的漸進式工具探索，以及回應過濾。

**What** Uber MCP Gateway 涵蓋 800+ 個 MCP server 與 5,000+ 個工具，供 AI agent 標準化地發現並呼叫內部服務。

### 重點
- 規模：800+ MCP server、5,000+ 工具，由單一 MCP Gateway 治理
- 設計：工具註冊與執行期呼叫分離，並有自動 API 探索與存取控制
- 防護與效率：敏感資料遮蔽、回應過濾，以及透過 Omni MCP 做漸進式工具探索

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/uber-mcp-gateway-ai-agents/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber has built an MCP Gateway to standardize how AI agents discover and invoke internal services across more than 800 MCP servers and 5,000 tools. The gateway separates tool registration from runtime execution and includes automated API discovery, access controls, sensitive data redaction, incremental tool discovery through Omni MCP, and response filtering. By Leela Kumili

</details>