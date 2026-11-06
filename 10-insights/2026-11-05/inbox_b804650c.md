---
id: inbox_b804650c
date: 2026-11-05
source_ref: "[[00-inbox/2026-11-05/0002-hermes-agent-releases-hermes-agent-v0-23-0-the-hearth-release-7a07]]"
title: "Hermes Agent v0.23.0 — The Hearth Release"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.0
source: hermes-agent-releases
published_at: 2026-11-05T21:32:33+00:00
fetched_at: 2026-11-06T00:13:38.701756+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓所有入口共用同一個 gateway 管理對話，避免各自執行 agent 造成訊息重複或遺失。 **Why** CLI、TUI、Desktop、編輯器、機器人與 cron 過去各自跑一份 agent，同一聊天可能被寫兩次或不見。 **How** 每台機器由單一 gateway 擁有所有 session，各介面以 client 身分連入，共用同一個佇列與歷史紀錄。 **What** v0.23.0 推出預設關閉的瀏覽器 Webapp、終端機內嵌圖片、/rewind 回溯對話，以及可同時連線多台機器的 Desktop；內建 skills 由 58 減為 44，舊的 browser_* 工具已移除，改用 browser_exec。"
key_points:
  - "單一 gateway 擁有所有 session，CLI、TUI、Desktop、ACP 編輯器、機器人與 cron 皆以 client 連入，同一聊天只有一個佇列與歷史"
  - "內建 skills 由 58 減為 44，Word、PowerPoint、Excel 合併為 microsoft-office；舊 browser_* 工具移除，需改用 browser_exec"
  - "外掛目錄由約 600 增至 1,050 以上；付費 MCP 工具可標示單次價格，聊天超過花費上限時會先詢問"
tags: [hermes-agent, release, gateway-architecture, browser-automation, mcp]
topics: [agents.coding_agents, agents.frameworks]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.23.0 — The Hearth Release

讓所有入口共用同一個 gateway 管理對話，避免各自執行 agent 造成訊息重複或遺失。

**Why** CLI、TUI、Desktop、編輯器、機器人與 cron 過去各自跑一份 agent，同一聊天可能被寫兩次或不見。

**How** 每台機器由單一 gateway 擁有所有 session，各介面以 client 身分連入，共用同一個佇列與歷史紀錄。

**What** v0.23.0 推出預設關閉的瀏覽器 Webapp、終端機內嵌圖片、/rewind 回溯對話，以及可同時連線多台機器的 Desktop；內建 skills 由 58 減為 44，舊的 browser_* 工具已移除，改用 browser_exec。

### 重點
- 單一 gateway 擁有所有 session，CLI、TUI、Desktop、ACP 編輯器、機器人與 cron 皆以 client 連入，同一聊天只有一個佇列與歷史
- 內建 skills 由 58 減為 44，Word、PowerPoint、Excel 合併為 microsoft-office；舊 browser_* 工具移除，需改用 browser_exec
- 外掛目錄由約 600 增至 1,050 以上；付費 MCP 工具可標示單次價格，聊天超過花費上限時會先詢問

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.23.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.23.0 
 Release Date: November 5, 2026 
 Since v0.22.0: ~10,080 commits · ~1,950 merged PRs · ~8,720 files changed · ~725,200 insertions · ~201,400 deletions · ~850 issues closed · 666 contributors 
 
 The Hearth Release. In the old hymns Hermes kept the threshold and Hestia kept the hearth, and the two were honored side by side. v0.22.0 got newcomers through the door; v0.23.0 builds the fire they gather around. The headline: your whole Desktop workspace now opens in a browser tab, served by your own gateway. Underneath it, every conversation lives in one place: a single gateway owns each session, and the CLI, TUI, Desktop, editors, bots and cron all sit down at the same table instead of each running its own agent. From that one hearth, Desktop keeps every machine you run Hermes on connected at once, Group Chats route their own conversations, and the terminal finally draws your images inline and lets you rewind a conversation. Around it: plugins that keep themselves updated, price tags and spend limits on paid MCP tools, pluggable delegation, a plugin catalog that grew from about 600 to over 1,050 entries, a leaner built-in skill set, and a long run of memory and latency work for long-lived gateways. This release rolls up and fully documents the v0.22.1–v0.22.7 patch releases. 
 

 
 ✨ Highlights 
 
 
 Your Desktop workspace in a browser tab — The new Webapp serves the full Desktop workspace from your own gateway: the same chats, Group Chats, plugins and settings, in any browser on your network or behind a public URL with sign-in. The Docker image and Nix package ship it. It is off by default; turn it on with webapp.enabled or Web Access in Settings. ( #141864 , #145598 , #145536 , #145072 , #145153 — @jquesnelle , @BearHuddleston , @IAvecilla , @Adolanium ) 
 
 
 One gateway owns every conversation — Before, the CLI, TUI, Desktop, editors (ACP), messaging bots and cron could each run their own copy of the agent against the same chat, which is how messages got written twice or went missing between surfaces. Now each machine runs one gateway that owns every session, and every surface attaches to it as a client: a chat you open anywhere is the same chat, with one queue and one history. You can even steer or edit a queued prompt from Desktop without it running twice. ( #106742 , #140334 — @unsupportedpastels , @kshitijk4poor ) 
 
 
 Pictures in the terminal — When you paste an image, or a tool takes a screenshot, the CLI and TUI now draw it right in the chat instead of printing a file path: real pixels in kitty and Ghostty (CLI and TUI) and in iTerm2, WezTerm and Konsole (CLI), coloured blocks everywhere else, and full resolution in VS Code's terminal when its image support is on. ( #147293 , #148874 — @Adolanium ) 
 
 
 Rewind a conversation — Press Esc twice or type /rewind in the TUI or classic CLI, pick an earlier message, then edit and resend it or fork a new session from that point. The original session stays exactly as it was. The TUI can also start /new while a turn is still running; the old one keeps working in the background. ( #144937 , #148880 — @SaguaroDev ) 
 
 
 Every machine in one Desktop window — Desktop now keeps all your gateways connected at once, so switching between this computer and an SSH or remote gateway is instant. Terminal tabs run on the host they were opened on, and a Group Chat can mix bots from different machines. ( #147681 , #147708 , #148418 — @dskwe , @janviernine ) 
 
 
 Group Chats that run themselves — Bot Mode rooms can let a lead bot, or an automatic router, pick who answers a message that names nobody. Scheduled jobs can post into a room, rooms keep a purpose and shared notes, and bots no longer ping each other in endless loops. Rooms also look like a normal Hermes chat now, and each bot shows what it is doing live ("scout · terminal · 7s"). ( #144833 , #148417 , #148888 , #148903 , #148422 — @KoNit-K ) 
 
 
 Plugins that keep themselves current — hermes plugins update updates everything at once, and an opt-in Auto-update switch (CLI, chat, Desktop and dashboard) keeps catalog and git plugins up to date. Updates that would break your setup are held back instead of applied. The catalog itself grew from about 600 to over 1,050 entries, and a new Verified tier marks plugins built by the vendor itself. ( #141513 , #85794 , #143468 , #144257 — @charan-rathore , @YS-OH-CORE ) 
 
 
 Price tags and spend limits for paid tools — Paid MCP tools, such as 3D or media generation, can declare what a call costs. The approval prompt shows each call's price and the chat's running total, and Hermes asks before a chat goes over its limit, even in YOLO mode. ( #142470 , #143780 , #143795 , #143787 — @liuhao1024 , @fangliquanflq ) 
 
 
 New official plugins, and a smaller core — Meshy (text and image to 3D), ElevenLabs Music and Sound Effects, X Chat, REA (reverse engineering) and a bubblewrap sandbox are now one-command installs. Camofox, mcp-serve , the agent importers and Singularity moved out of core into plugins that install themselves for anyone who used them. ( #142619 , #146294 , #139725 , #143484 , #139983 ) 
 
 
 Choose how subagents are run — Delegation is now pluggable: keep the default, or install the official advanced-delegation plugin to send each subagent task to a named model or into a separate profile. Switch with /delegation . ( #142563 , #142564 , #143423 ) 
 
 
 Lighter and faster, especially when Hermes runs all day — Recurring cron jobs share a prompt cache, one-shot runs send about 1,570 fewer prompt tokens per call, and patch / write_file return in milliseconds with LSP on. Long-lived gateways now let go of closed sessions' memory, and the Desktop sidebar no longer slows down as sessions pile up (one store with ~35k cron runs went from a 121 s refresh to instant). ( #139876 , #144177 , #140387 , #147863 , #137087 , #147819 , #144940 — @kshitijk4poor ) 
 
 
 A leaner skill set you can lock — The built-in skills went from 58 to 44, with Word, PowerPoint and Excel merged into one microsoft-office skill. hermes curator lock stops the agent from rewriting a skill you curated by hand, through any tool, even in YOLO mode. ( #147557 — @daviseford ) 
 
 
 Password managers and a keychain vault key — Verified password-manager plugins can hand the browser your logins without seeing anyone else's, and the browser vault's key can now live in your OS keychain. ( #143964 , #144246 — @Jesssullivan ) 
 
 
 Stop a running cron job — Cancel a running job from the CLI, Desktop, the API or the agent itself, and set per job what happens to runs missed while Hermes was off. ( #144801 — @kokhlo , @fangliquanflq , @LeonSGP43 ) 
 
 
 ⚠️ Upgrade notes 
 
 The old built-in browser tools are gone. Browser automation runs on browser_exec only; agent-browser and the ten browser_* tools ( browser_navigate , browser_click , ...) were removed. Homes that used Camofox get the camofox plugin installed automatically. If your own prompts, skills or toolset lists name the old tools, switch them to browser_exec . ( #143146 ) 
 Desktop needs macOS 13+ and 64-bit Windows. The app moved to Electron 44, which no longer runs on macOS 11, macOS 12 or 32-bit Windows. ( #142727 — @OutThisLife , @Adihaliem ) 
 hermes mcp serve is now hermes mcp-serve (it moved into a plugin). MCP clients that launch Hermes as a server need their command updated; nothing rewrites it for you. 
 Word, PowerPoint and Excel skills are now one microsoft-office skill. Old copies stay on disk until you remove them. 
 The Webapp is off by default. Nothing is served to a browser until you turn on webapp.enabled or Web Access. 
 
 🧠 Core Agent, Gateway & Tools 
 Providers & Models 
 
 GLM-5.3 is the default model when you never pick one — The silent default moves from GLM-5.2 to GLM-5.3, at about the same price and with the same 1M context window on Nous Portal and OpenRouter. ( #144810 — @calvinnwq ) 
 New models — GPT-6.1 Terra, DeepSeek V4.1 Flash 1017 and Gemini 4 Argon on Solstice. Claude Mythos is treated as always-thinking, so reasoning-off requests stop failing their first try. Nemotron 3.5 Super VL gets default parameters. ( #145204 , #140496 , #139466 , #148127 , #138462 — @benbarclay , @unsupportedpastels , @rroverin ) 
 Usage-window plans — On subscriptions that track usage as allowances instead of credits, /usage shows one bar per allowance with its reset time. Pickers list the plan's recommended models first, tag them Large or Free, and say when an allowance has run out. ( #142308 , #145682 — @rob-maron ) 
 Daybreak for approved ChatGPT subscriptions — An off-by-default agent.daybreak switch turns on OpenAI's Trusted Access for Cyber program. It only appears on models that your account's own Codex catalog lists as approved, and it is checked again on every request. ( #148056 — @unsupportedpastels , @Froraut ) 
 /model reset — Takes a session pinned with /model back to your configured default without losing the conversation, in the CLI, TUI, Desktop and messaging. ( #80448 — @shannonsands ) 
 GitHub Copilot moved to a labs plugin — Copilot ( copilot , copilot-acp ) now lives in the github-copilot Hermes Labs plugin, which profiles that use Copilot install automatically. Core keeps generic provider hooks that any provider plugin can use. ( #144788 ) 
 Custom endpoints resolve reliably — New profiles inherit custom: , ${VAR} and legacy custom endpoints instead of failing with "Unknown provider". Resumed chats stay on the endpoint that served them, and a built-in provider's key no longer leaks onto a custom entry with the same name. ( #138513 , #139947 , #140335 , #147761 — @jquesnelle , @unsupportedpastels ) 
 Provider quirks handled — Streamed tool calls from LM Studio, Kimi and MiniMax no longer split into broken calls. Gemini safety blocks now show as a content-policy error and move on to the fallback model. Text-only vLLM servers that reject images recover, and byte-cap 400s trigger compression. On Bedrock, a hung call fails after one read timeout instead of five. ( #140485 , #85031 , #85005 , #85126 , #146314 — @Chukwuebuka-2003 ) 
 Local runtime on llama.cpp b11671 — Adds one-slot DFlash drafts and opt-in Nemotron 3.5 Bolt. ( #139703 — @jquesnelle ) 
 
 Agent Loop & Sessions 
 
 Lower prompt-token and cache costs — Every fire of the same cron job now shares one prompt-cache key. Background one-shot calls (summaries, titles, /moa ) stop paying for cache writes. One-shot runs send 1,570 fewer prompt tokens per call, and four tool schemas are 319 tokens shorter. Gateway goal and heartbeat turns, post-compaction turns and between-turn MCP refreshes no longer rewrite the cached prefix. ( #139876 , #140478 , #144177 , #144173 , #139865 , #139851 — @100yenadmin , @jonpol01 , @chelsealong , @AdrianBinDC ) 
 Opt-in prepared compaction — With compression.prepare_ahead: true , the next summary is written in the background as a session nears the trigger, so compaction no longer pauses the turn while the summary is written. Messages that arrive in the meantime stay in the tail word for word. Off by default. ( #144684 , #144886 — @kshitijk4poor ) 
 Compaction is more honest and harder to stall — Summaries list uncertain claims on UNVERIFIED: lines, so a guess does not come back as a fact. The main-model fallback uses the main route, /stop closes a summary stream, and queued messages and /steer survive a context-exhaustion reset. ( #86019 , #139872 , #144825 , #139783 , #139923 — @helix4u , @thehugegatsby ) 
 hermes sessions refresh-prompts — Continuing sessions pick up an edited SOUL.md , skills or context files on their next turn without /new . History is kept and each session takes one cache miss. ( #143581 — @victor-kyriazakos ) 
 Opt-in stream lifetime cap — agent.stream_max_lifetime (off by default) cuts off a stream that never finishes. Timeout errors now name the phase that failed and the setting to raise. ( #80701 , #80873 — @krzsda ) 
 Follow-up questions about a photo still s

[... truncated for safety ...]

</details>