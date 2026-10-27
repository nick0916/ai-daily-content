---
id: inbox_b4c8150b
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/0125-github-trending-agent-tools-nightly-labs-openbot-1-492-176-ed92]]"
title: "nightly-labs/openbot ⭐ 1,492(今日 +176)"
url: https://github.com/nightly-labs/openbot
source: github-trending-agent-tools
published_at: 2026-10-27T01:25:27.449568+00:00
fetched_at: 2026-10-27T01:38:32.587885+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一個本地優先的桌面工作區，讓多個 AI agent 各自擁有工作區與對話，並可彼此傳訊協作。 **What** 支援本地 Codex App Server 與 Claude Code，並經 ACP 支援 Grok CLI、OpenCode、Gemini、Cursor CLI 與 Cline CLI；內建本地任務佇列、檔案傳輸、內嵌瀏覽器與 agent 間訊息。目前為開發預覽版，agent 以 danger-full-access 與 approvalPolicy: never 執行，首次啟動同意後無逐項確認。GitHub 星數約 1,492（今日 +176）。"
key_points:
  - "平台：macOS 13+、Windows 10+（x64）與 Linux AppImage；另可用 VPS（Ubuntu 24.04/26.04 systemd）或 Docker 以伺服器模式執行"
  - "安全警示：agent 可讀寫檔案、執行指令、使用網路與內嵌瀏覽器，且無逐項確認；README 建議只執行信任的 agent 與任務"
  - "Provider CLI 可由 OpenBot 下載並固定版本；OpenCode Go 付費模型需另以 key 登入"
tags: [ai-agents, desktop-app, agent-collaboration, local-first, acp]
topics: [agents.coding_agents, security]
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## nightly-labs/openbot ⭐ 1,492(今日 +176)

一個本地優先的桌面工作區，讓多個 AI agent 各自擁有工作區與對話，並可彼此傳訊協作。

**What** 支援本地 Codex App Server 與 Claude Code，並經 ACP 支援 Grok CLI、OpenCode、Gemini、Cursor CLI 與 Cline CLI；內建本地任務佇列、檔案傳輸、內嵌瀏覽器與 agent 間訊息。目前為開發預覽版，agent 以 danger-full-access 與 approvalPolicy: never 執行，首次啟動同意後無逐項確認。GitHub 星數約 1,492（今日 +176）。

### 重點
- 平台：macOS 13+、Windows 10+（x64）與 Linux AppImage；另可用 VPS（Ubuntu 24.04/26.04 systemd）或 Docker 以伺服器模式執行
- 安全警示：agent 可讀寫檔案、執行指令、使用網路與內嵌瀏覽器，且無逐項確認；README 建議只執行信任的 agent 與任務
- Provider CLI 可由 OpenBot 下載並固定版本；OpenCode Go 付費模型需另以 key 登入

**原文：** [github-trending-agent-tools](https://github.com/nightly-labs/openbot)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A local-first desktop workspace for persistent AI teammates. Run Codex, Claude, and Grok with dedicated workspaces, task queues, file sharing, browser control, and agent-to-agent collaboration.

OpenBot

What works

Install

Development

Local skills

Import agents from Grok Bot

Commands

Architecture

Chat attachments

Local data and network boundaries

Security

Releases

Contributing

License and attribution

macOS

Windows

Linux

Nix

Agent setup

Marketplace launch catalog

macOS remote desktop permissions

Shared macOS hosts

OpenBot is a local-first desktop workspace for persistent AI teammates. It supports the local Codex App Server and Claude Code , plus Grok CLI ,
OpenCode, Gemini, Cursor CLI , and Cline CLI through ACP. It gives every agent its own workspace and
conversation, and provides local queues, file transfers, an embedded browser, and agent-to-agent
messaging in one desktop app.

Warning

OpenBot is a development preview. Agents currently run with danger-full-access and approvalPolicy: never . They can read and modify files, run commands, use the network, and control
the embedded browser without per-action confirmations after the explicit first-launch consent.
Run only agents and tasks you trust, keep backups, and review Security before use.

OpenBot is local-first, not offline-only. Codex connects to OpenAI, Claude connects to Anthropic,
Grok connects to xAI, Gemini connects to Google, Cursor connects to Cursor, Cline connects to Cline,
visited pages use the network, and installed plugins may connect to their own services.

OpenBot supports macOS 13 or newer on Apple silicon or Intel, Windows 10 or newer on x64 systems, and x64
or arm64 Linux as an AppImage.

The AppImage does not need libfuse2, so it also runs on Arch Linux and Omarchy. It mounts itself
with fusermount3 from the fuse3 package.

On Ubuntu 23.10 or newer and on Debian 13, unprivileged user namespaces are restricted by AppArmor
and OpenBot exits during launch until you install an AppArmor profile:

The same file ships inside the AppImage at resources/linux/openbot.apparmor . Edit the attachment
path in the profile if you keep the AppImage outside the usual locations. Do not start OpenBot with --no-sandbox : that removes the boundary between a renderer and the rest of the computer.

On the first start from an AppImage, OpenBot writes ~/.local/share/applications/openbot.desktop and ~/.local/share/icons/openbot.png , which is what lets an openbot:// link - an invitation, or
a plugin listing - open the app and gives the launcher an icon that stays after the app exits. Delete the two files to undo it.

Remote desktop works on Linux x64 in an X11 session,
such as Xorg or Xvfb. It does not work under Wayland, and the arm64 AppImage does not include it.

For Gemini sign-in, install a desktop browser and xdg-utils . Open the sign-in page in a
desktop session on the same host or VM. Google sends the callback to that host through 127.0.0.1 ; a server with no desktop cannot complete this sign-in. See Gemini setup .

To run OpenBot as an always-on server of your account on a VPS or home server (Ubuntu 24.04 or
26.04 with systemd), install it from a terminal and sign in with an email code:

Then use it from the desktop app, the iPhone app or openbot.run/app . See self-hosted servers for the options and the openbot commands.

The same server runs as a container ( linux/amd64 and linux/arm64 ). The seccomp profile lets the
Electron sandbox stay on:

See Docker for Compose, the data volume, upgrades and the security limits. For Amazon ECS,
see AWS ECS .

The flake installs the desktop app from the latest release on x64 or arm64 Linux and on Apple silicon:

overlays.default adds pkgs.openbot . OpenBot is not free software, so your nixpkgs must allow it,
for example with nixpkgs.config.allowUnfreePredicate = pkg: lib.getName pkg == "openbot"; .
Nix installs OpenBot updates. OpenBot does not update itself from the Nix store. On Linux, the Nix
package does not include the remote desktop runtime, because nixpkgs does not have a library that it
needs.

Important

Windows releases are signed by SYNTHETIFY LABS SPÓŁKA Z OGRANICZONĄ ODPOWIEDZIALNOŚCIĄ . Older
releases are not code-signed. SmartScreen can still warn about a new release. Check the release
checksum or GitHub build attestation before you run the installer.

OpenBot can download a supported provider runtime when you select Download in onboarding,
Settings, agent setup, or the model picker. OpenBot prefers its managed CLI. Explicit OPENBOT_*_PATH overrides take precedence; a compatible
system CLI is used when no managed copy is available. OpenBot checks for a newer provider CLI
release at startup and every hour, and Check for updates in a provider's actions menu checks at
once. Updates install the latest upstream release without changing the user’s system CLI; the
version in native-runtime.lock.json is only the first-install fallback.

You can also install a CLI yourself.

Codex CLI on macOS:

Claude CLI on macOS:

Install Grok CLI following the Grok Build documentation , then
authenticate with grok login or set XAI_API_KEY in the environment used to launch OpenBot.

OpenBot downloads and pins the OpenCode CLI, like Codex, Claude, and Grok. OpenCode's free models
need no account and no sign-in: select OpenCode, click Connect, and OpenBot reads the models that
the CLI advertises. To use the paid OpenCode Go models, click Sign in on the OpenCode row and
paste a Go key from opencode.ai/auth . OpenBot encrypts the key on this
computer and gives it only to the local CLI. OpenBot supports OpenCode Go only: the Zen models a
Go key does not buy stay out of the picker. Models with the Free label in the model picker need no
sign-in. Other models need a sign-in with their provider: a Go key for the opencode-go/ models, or opencode auth login in a terminal for OpenCode Zen and third-party providers. Without it, the turn
fails with an error that names the provider. If you installed OpenCode yourself, OpenBot
keeps that install and offers no download. Set OPENBOT_OPENCODE_PATH to select an executable
outside your shell's search path. Remote OpenCode agents require Team A

</details>