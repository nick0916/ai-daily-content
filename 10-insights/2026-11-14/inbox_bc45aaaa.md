---
id: inbox_bc45aaaa
date: 2026-11-14
source_ref: "[[00-inbox/2026-11-14/0147-github-trending-agent-tools-chromedevtools-chrome-devtools-mcp-55-47-3fb2]]"
title: "ChromeDevTools/chrome-devtools-mcp ⭐ 55,472(今日 +67)"
url: https://github.com/ChromeDevTools/chrome-devtools-mcp
source: github-trending-agent-tools
published_at: 2026-11-14T01:47:24.130076+00:00
fetched_at: 2026-11-14T01:57:58.079988+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 coding agent 透過 MCP 與 CLI 直接操控並檢視正在執行的 Chrome。 **Why** 原文說明此工具用於讓代理人可靠地自動化操作、深入除錯與分析效能。 **How** 以 Puppeteer 自動化瀏覽器動作並等待結果，同時透過 Chrome DevTools 取得效能 trace、網路請求、console 訊息（含 source-mapped stack）與截圖。 **What** GitHub 星數 55,472（今日 +67），可用 Claude Code 的 `/plugin install` 一次安裝 MCP 與 skills；預設會把 trace URL 送至 CrUX API 並回報使用統計，可用 `--no-performance-crux` 與 `--no-usage-statistics` 關閉。"
key_points:
  - "同時提供 MCP server 與 chrome-devtools CLI 兩種入口，並附 skills 教 agent 正確呼叫工具"
  - "效能分析時 trace URL 會送至 Google CrUX API，使用統計預設開啟，需以旗標或環境變數關閉"
  - "官方僅支援 Google Chrome 與 Chrome for Testing，需 Node.js LTS 與 Chrome 最新穩定版"
tags: [mcp, chrome, devtools, browser-automation, coding-agents]
topics: [agents.mcp, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## ChromeDevTools/chrome-devtools-mcp ⭐ 55,472(今日 +67)

讓 coding agent 透過 MCP 與 CLI 直接操控並檢視正在執行的 Chrome。

**Why** 原文說明此工具用於讓代理人可靠地自動化操作、深入除錯與分析效能。

**How** 以 Puppeteer 自動化瀏覽器動作並等待結果，同時透過 Chrome DevTools 取得效能 trace、網路請求、console 訊息（含 source-mapped stack）與截圖。

**What** GitHub 星數 55,472（今日 +67），可用 Claude Code 的 `/plugin install` 一次安裝 MCP 與 skills；預設會把 trace URL 送至 CrUX API 並回報使用統計，可用 `--no-performance-crux` 與 `--no-usage-statistics` 關閉。

### 重點
- 同時提供 MCP server 與 chrome-devtools CLI 兩種入口，並附 skills 教 agent 正確呼叫工具
- 效能分析時 trace URL 會送至 Google CrUX API，使用統計預設開啟，需以旗標或環境變數關閉
- 官方僅支援 Google Chrome 與 Chrome for Testing，需 Node.js LTS 與 Chrome 最新穩定版

**原文：** [github-trending-agent-tools](https://github.com/ChromeDevTools/chrome-devtools-mcp)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Chrome DevTools for coding agents

Chrome DevTools for agents

Key features

Disclaimers

Usage statistics

Update checks

Requirements

Getting started

CLI

Skills

Tools

Configuration

Advanced Usage

Integrating as a browser subagent

MCP Client configuration

Your first prompt

Install skills as a plugin

Install skills manually

Keep skills up to date

Chrome DevTools for agents ( chrome-devtools-mcp ) lets your coding agent (such as Antigravity, Claude, Cursor or Copilot)
control and inspect a live Chrome browser. It is available as a
Model-Context-Protocol (MCP) server and as a CLI . Both give your AI
coding assistant access to the full power of Chrome DevTools for reliable
automation, in-depth debugging, and performance analysis.

Tool reference | CLI | Skills | Changelog | Contributing | Troubleshooting | Design Principles

chrome-devtools-mcp exposes content of the browser instance to the MCP clients
allowing them to inspect, debug, and modify any data in the browser or DevTools.
Avoid sharing sensitive or personal information that you don't want to share with
MCP clients.

chrome-devtools-mcp officially supports Google Chrome and Chrome for Testing only.
Other Chromium-based browsers may work, but this is not guaranteed, and you may encounter unexpected behavior. Use at your own discretion.
We are committed to providing fixes and support for the latest version of Extended Stable Chrome .

Performance tools may send trace URLs to the Google CrUX API to fetch real-user
experience data. This helps provide a holistic performance picture by
presenting field data alongside lab data. This data is collected by the Chrome
User Experience Report (CrUX) . To disable
this, run with the --no-performance-crux flag.

Google collects usage statistics (such as tool invocation success rates, latency, and environment information) to improve the reliability and performance of Chrome DevTools MCP.

Data collection is enabled by default . You can opt-out by passing the --no-usage-statistics flag when starting the server:

Google handles this data in accordance with the Google Privacy Policy .

Google's collection of usage statistics for Chrome DevTools MCP is independent from the Chrome browser's usage statistics. Opting out of Chrome metrics does not automatically opt you out of this tool, and vice-versa.

Collection is disabled if CHROME_DEVTOOLS_MCP_NO_USAGE_STATISTICS or CI env variables are set.

By default, the server periodically checks the npm registry for updates and logs a notification when a newer version is available.
You can disable these update checks by setting the CHROME_DEVTOOLS_MCP_NO_UPDATE_CHECKS environment variable.

Add the following config to your MCP client:

Note

Using chrome-devtools-mcp@latest ensures that your MCP client will always use the latest version of the Chrome DevTools MCP server.

For setup instructions specific to your editor or agent (e.g. Antigravity, Claude Code, Cursor, VS Code), please see our Client Configurations Guide .

Enter the following prompt in your MCP Client to check if everything is working:

Your MCP client should open the browser and record a performance trace.

Note

The MCP server will start the browser automatically once the MCP client uses a tool that requires a running browser instance. Connecting to the Chrome DevTools MCP server on its own will not automatically start the browser.

The package also includes the chrome-devtools CLI. Use it to control the browser from your terminal without MCP:

See the CLI guide for all commands and options.

The package includes skills that teach your agent how to use Chrome DevTools:

A plugin installs the MCP server and all skills, including the CLI skill:

See the Client Configurations Guide for more information.

If your agent does not support plugins, copy the skill folders into the skills directory of your agent. The npm package contains the skills:

Important

The chrome-devtools-cli skill requires the CLI. Install the package globally before you use the skill.

Skills describe the tools of a specific version. Update the skills each time you update the MCP server or the CLI. Outdated skills can tell your agent to use tools or parameters that changed.

If you run into any issues, checkout our troubleshooting guide .
See the full Tool Reference for a complete list of all supported MCP capabilities.

Find the complete list of server parameters (e.g., --headless , --isolated , --slim ) and how to configure WebSocket connections in the Configuration Guide .

For basic browser tasks only, the --slim flag exposes a reduced set of tools. See the Slim tool reference .

For advanced features such as handling concurrent sessions, persistent user data directories, using a custom or non-standard browser path ( --executablePath ), connecting to a running Chrome instance instead of starting a new one, or debugging on Android, see our Advanced Usage Guide .

If you are developing agentic tooling and want to provide an integrated browser subagent as part of your product, we recommend building on top of Chrome DevTools for agents.

For a reference implementation, see the Gemini CLI browser agent documentation .

Get performance insights : Uses Chrome
DevTools to record
traces and extract actionable performance insights.

Advanced browser debugging : Analyze network requests, take screenshots and
check browser console messages (with source-mapped stack traces).

Reliable automation . Uses puppeteer to automate actions in
Chrome and automatically wait for action results.

Node.js LTS version.

Chrome current stable version or newer.

npm

Claude Code: Run /plugin marketplace add ChromeDevTools/chrome-devtools-mcp , then /plugin install chrome-devtools-mcp@chrome-devtools-plugins .

Copilot / VS Code: Run Chat: Install Plugin From Source and enter ChromeDevTools/chrome-devtools-mcp .

Gemini CLI: Run gemini extensions install --auto-update https://github.com/ChromeDevTools/chrome-devtools-mcp .

Plugins: Use the update command of the plugin man

</details>