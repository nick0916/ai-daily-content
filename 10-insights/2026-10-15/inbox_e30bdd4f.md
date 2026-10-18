---
id: inbox_e30bdd4f
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-substack-byte-sized-design-uber-put-5-000-tools-in-front-of-its-age-a7b6]]"
title: "🚪 Uber Put 5,000 Tools in Front of Its Agents. Every One Ships Switched Off."
url: https://read.bytesizeddesign.com/p/uber-mcp-gateway-5000-tools-switched-off
source: substack-byte-sized-design
published_at: 2026-10-15T05:32:30+00:00
fetched_at: 2026-10-18T03:13:33.122163+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Byte-Sized Design 報導 Uber 把 5,000 個 tool 放到其 agent 面前，且每個 tool 預設都是關閉狀態。原文摘要指出，800 多個 MCP server 集中在單一 gateway 之後，由 crawler 產出草稿，再由人工核准。這代表工具的上架流程是自動探索加人工把關，而不是讓 agent 自行取用全部工具。實務意義是，企業在大規模暴露 MCP 工具時，可採用「預設關閉、經核准才開啟」的治理方式。更細的 gateway 架構與核准流程，提供的內容沒有說明。

```mermaid
flowchart LR
  A[Crawler 掃描 MCP servers] --> B[產生 tool 草稿]
  B --> C[人工核准]
  C --> D[MCP Gateway 800+ servers]
  D --> E[Agents 使用已開啟的 tools]
```"
key_points:
  - "Uber 的單一 gateway 後方有 800 多個 MCP server、共 5,000 個 tool"
  - "每個 tool 預設為關閉，由 crawler 產出草稿、人工核准後才開啟"
tags: [uber, mcp-gateway, tool-governance, default-off]
topics: [agents.mcp, security]
importance: 3
novelty: 4
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## 🚪 Uber Put 5,000 Tools in Front of Its Agents. Every One Ships Switched Off.

Byte-Sized Design 報導 Uber 把 5,000 個 tool 放到其 agent 面前，且每個 tool 預設都是關閉狀態。原文摘要指出，800 多個 MCP server 集中在單一 gateway 之後，由 crawler 產出草稿，再由人工核准。這代表工具的上架流程是自動探索加人工把關，而不是讓 agent 自行取用全部工具。實務意義是，企業在大規模暴露 MCP 工具時，可採用「預設關閉、經核准才開啟」的治理方式。更細的 gateway 架構與核准流程，提供的內容沒有說明。

```mermaid
flowchart LR
  A[Crawler 掃描 MCP servers] --> B[產生 tool 草稿]
  B --> C[人工核准]
  C --> D[MCP Gateway 800+ servers]
  D --> E[Agents 使用已開啟的 tools]
```

### 重點
- Uber 的單一 gateway 後方有 800 多個 MCP server、共 5,000 個 tool
- 每個 tool 預設為關閉，由 crawler 產出草稿、人工核准後才開啟

**原文：** [substack-byte-sized-design](https://read.bytesizeddesign.com/p/uber-mcp-gateway-5000-tools-switched-off)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

800+ MCP servers behind one gateway, drafted by a crawler and approved by humans

</details>