---
id: inbox_b375f777
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2318-github-trending-agent-tools-cursor-plugins-16-881-196-9fd4]]"
title: "cursor/plugins ⭐ 16,881(今日 +196)"
url: https://github.com/cursor/plugins
source: github-trending-agent-tools
published_at: 2026-11-17T23:18:24.242549+00:00
fetched_at: 2026-11-17T23:29:56.398108+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cursor 官方的外掛市集倉庫，每個外掛都是根目錄下的獨立目錄。 **Why** 原文說明這是為熱門開發工具、框架與 SaaS 提供的官方 Cursor 外掛。 **How** 根目錄 .cursor-plugin/marketplace.json 列出所有外掛，每個外掛另有自己的 plugin.json，並可包含 skills/（SKILL.md）、rules/（.mdc）與 mcp.json。 **What** 專案採 MIT 授權，今日 GitHub 星數 16,881（+196）；輸入內容只有結構說明，未列出具體外掛名稱與數量。"
key_points:
  - "根目錄 marketplace.json 列出所有外掛，每個外掛有自己的 .cursor-plugin/plugin.json"
  - "單一外掛可含 skills（SKILL.md）、rules（.mdc）、mcp.json（MCP 伺服器定義），並附 README、CHANGELOG、LICENSE"
  - "原文 body 未列出具體外掛名稱，無法判斷涵蓋哪些工具"
tags: [cursor, plugins, marketplace, mcp, agent-skills]
topics: [agents.coding_agents, agents.mcp]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## cursor/plugins ⭐ 16,881(今日 +196)

Cursor 官方的外掛市集倉庫，每個外掛都是根目錄下的獨立目錄。

**Why** 原文說明這是為熱門開發工具、框架與 SaaS 提供的官方 Cursor 外掛。

**How** 根目錄 .cursor-plugin/marketplace.json 列出所有外掛，每個外掛另有自己的 plugin.json，並可包含 skills/（SKILL.md）、rules/（.mdc）與 mcp.json。

**What** 專案採 MIT 授權，今日 GitHub 星數 16,881（+196）；輸入內容只有結構說明，未列出具體外掛名稱與數量。

### 重點
- 根目錄 marketplace.json 列出所有外掛，每個外掛有自己的 .cursor-plugin/plugin.json
- 單一外掛可含 skills（SKILL.md）、rules（.mdc）、mcp.json（MCP 伺服器定義），並附 README、CHANGELOG、LICENSE
- 原文 body 未列出具體外掛名稱，無法判斷涵蓋哪些工具

**原文：** [github-trending-agent-tools](https://github.com/cursor/plugins)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Cursor plugin specification and official plugins

Cursor plugins

Plugins

Repository structure

License

Official Cursor plugins for popular developer tools, frameworks, and SaaS products. Each plugin is a standalone directory at the repository root with its own .cursor-plugin/plugin.json manifest.

This is a multi-plugin marketplace repository. The root .cursor-plugin/marketplace.json lists all plugins, and each plugin has its own manifest:

MIT

plugins/
├── .cursor-plugin/
│ └── marketplace.json # Marketplace manifest (lists all plugins)
├── plugin-name/
│ ├── .cursor-plugin/
│ │ └── plugin.json # Per-plugin manifest
│ ├── skills/ # Agent skills (SKILL.md with frontmatter)
│ ├── rules/ # Cursor rules (.mdc files)
│ ├── mcp.json # MCP server definitions
│ ├── README.md
│ ├── CHANGELOG.md
│ └── LICENSE
└── ...

</details>