---
id: inbox_93a9384d
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2342-github-trending-agent-tools-homeassistant-ai-ha-mcp-5-935-31-a464]]"
title: "homeassistant-ai/ha-mcp ⭐ 5,935(今日 +31)"
url: https://github.com/homeassistant-ai/ha-mcp
source: github-trending-agent-tools
published_at: 2026-11-09T23:42:19.272704+00:00
fetched_at: 2026-11-10T00:09:00.789919+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ha-mcp 讓 Claude、ChatGPT 等 AI 助理透過 MCP 設定與自動化 Home Assistant。 **How** 提供 Home Assistant 自訂元件、HA app、Docker/PyPI、本地 stdio 等安裝方式，各方式都提供相同的 server。 **What** GitHub 趨勢頁今日 ⭐5,935（今日 +31）；README 所列設定流程適用 v9.0.0；v7.3.0 起 ha_config_set_yaml 移至 beta。"
key_points:
  - "每個 AI client 只保留一種安裝方式，同一 server 的多個 entry 是連線卡住的已知原因"
  - "custom component 內建 webhook 供遠端存取，不需 Webhook Proxy"
  - "README 指出 stdio 有連線問題（#1713），建議僅用於測試"
tags: [home-assistant, mcp, smart-home, github-trending]
topics: [agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## homeassistant-ai/ha-mcp ⭐ 5,935(今日 +31)

ha-mcp 讓 Claude、ChatGPT 等 AI 助理透過 MCP 設定與自動化 Home Assistant。

**How** 提供 Home Assistant 自訂元件、HA app、Docker/PyPI、本地 stdio 等安裝方式，各方式都提供相同的 server。

**What** GitHub 趨勢頁今日 ⭐5,935（今日 +31）；README 所列設定流程適用 v9.0.0；v7.3.0 起 ha_config_set_yaml 移至 beta。

### 重點
- 每個 AI client 只保留一種安裝方式，同一 server 的多個 entry 是連線卡住的已知原因
- custom component 內建 webhook 供遠端存取，不需 Webhook Proxy
- README 指出 stdio 有連線問題（#1713），建議僅用於測試

**原文：** [github-trending-agent-tools](https://github.com/homeassistant-ai/ha-mcp)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Configure and automate Home Assistant with Claude, ChatGPT, and other AI assistants.

HA-MCP — Manage Home Assistant with AI

🚀 Get Started

💬 What Can You Do With It?

✨ Features

🆚 ha-mcp vs. Home Assistant's built-in MCP Server

🔌 Custom Component (ha_mcp_tools) — File & YAML Services

🧠 Better Results with Agent Skills

🔍 Tool Discovery for AI Agents

🧪 Dev Channel

🤝 Contributing

🔒 Privacy

📄 License

🙏 Acknowledgments

👥 Contributors

💬 Community

Star History

🏠 Home Assistant app (add-on)

Other install methods

🧪 Demo server (Windows / macOS / Linux)

🧙 Setup Wizard for 15+ clients

Install

Bundled Skills (built-in)

Smaller or local LLMs (Ollama, etc.)

Enable search-based discovery

When to enable

Per-URL tool catalog

Read-only HTTP connections

Maintainers

Contributors

Breaking change (v7.3.0): ha_config_set_yaml has been moved to beta .

 

 Configure and automate Home Assistant with Claude, ChatGPT, and other AI assistants. 

The recommended way to run ha-mcp is the HA-MCP integration . It installs into Home Assistant through HACS (the built-in Marketplace on Home Assistant 2026.11+), runs the full server in-process , and works on every Home Assistant installation type — Home Assistant OS, Supervised, Container, and Core — with full feature parity. It is the easiest setup in every case: setup asks for an administrator access token and how clients may connect.

Add it to Home Assistant via HACS or, on Home Assistant 2026.11+, the Marketplace (the preferred install):

Quick start:

The setup below is for version 9.0.0 (October 28, 2026) and later; earlier versions show a shorter setup form without the administrator account step.

Connect URL. The Configure screen gives you a Home Assistant webhook URL for remote clients — https:// /api/webhook/ through Nabu Casa or any reverse proxy already pointed at Home Assistant (locally, http:// :8123/api/webhook/ ). For clients on the same network, the server is also reachable directly at http:// :9584/private_ .

The component's second entry type, the File & YAML services entry ( HA-MCP File & YAML Tools ), is only needed if you enable ha-mcp's opt-in file and YAML editing tools (feature flags, off by default) — skip it otherwise; you can add it later at any time. It works with any server type (in-process, app, Docker, or stdio).

Full in-process server documentation → · Setup Wizard for client-specific config →

Prefer to run ha-mcp as a Home Assistant app (add-on) ? On Home Assistant OS and Supervised installs it is a close second — no access token to manage, and it works with Claude Desktop, Claude.ai, ChatGPT, and any other MCP client on your local network or configured for remote access.

Add the repository to your Home Assistant instance:

If that opens the App store without an add-repository dialog (a known Home Assistant issue ), add it manually: Settings → Apps → Install app → ⋮ → Repositories , then paste https://github.com/homeassistant-ai/ha-mcp .

Install "Home Assistant MCP Server" from Settings → Apps → Install app and click Start . (Home Assistant 2026.2 renamed "Add-ons" to "Apps"; on older versions this is the Add-on store.)

Open the Logs tab to find your unique MCP URL.

Connect your AI client to that URL — no token or credential setup needed .

Full app documentation →

⚠️ Configure exactly one install method per client. The custom component, the app, Docker/PyPI, and local stdio are independent ways to run the same server — pick one and point your AI client at that single URL. Keeping two entries for the same server in one client (for example a local uvx ha-mcp@latest entry with HOMEASSISTANT_URL / HOMEASSISTANT_TOKEN alongside an app or component URL) is a known cause of connection hangs.

These run the server outside Home Assistant — useful for Container / Core installs (which can't run apps) or a separate host. The Setup Wizard generates the exact client-specific config for each.

Docker (HTTP server): run ghcr.io/homeassistant-ai/ha-mcp in HTTP mode, pointed at your Home Assistant URL and a long-lived token (an administrator's is recommended; non-admin tokens work with limitations), and connect your client to its secret URL. See the Setup Wizard for the full command and per-client config.

PyPI / uvx (HTTP server): run the published ha-mcp package with uvx ha-mcp@latest (or pip) as a streamable-HTTP server the same way. Details in the Setup Wizard .

Local stdio (not recommended): runs ha-mcp on your own machine over stdio. The one-command installers in the Demo server section below use this path; the Setup Wizard covers connecting it to your own Home Assistant.

OIDC authentication: gate remote access behind an external identity provider (Authentik, Keycloak, Auth0, etc.) instead of a secret URL — all authenticated users share the server's Home Assistant credentials. See OIDC Mode .

⚠️ stdio has known transport issues. The stdio transport has connection problems that streamable HTTP does not ( #1713 ). It is recommended only for demo/testing tinkering — for a real setup, use the custom component or an HTTP method above.

Using the HA-MCP custom component? You do not need the Webhook Proxy — the component has its own built-in webhook for remote access (see the Get Started quick start at the top). The proxy is for the app (it can also front another external server via its mcp_server_url option). The OpenAI Tunnel below is different: it applies to any install method when Home Assistant isn't publicly reachable at all (no Nabu Casa or reverse proxy).

Already have Nabu Casa or another reverse proxy pointing at your Home Assistant? The Webhook Proxy app routes MCP traffic through your existing setup — no separate tunnel or port forwarding needed.

For other remote access methods (Cloudflare Tunnel, custom reverse proxy), see the Setup Wizard .

ChatGPT / Codex behind a firewall (OpenAI Tunnel). ChatGPT connectors normally require a publicly reachable URL. If you can't (or don't want to) expose one, the community OpenAI

</details>