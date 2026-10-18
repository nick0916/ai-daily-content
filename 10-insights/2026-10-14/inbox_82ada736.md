---
id: inbox_82ada736
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0256-hermes-agent-releases-hermes-agent-v0-22-0-the-threshold-relea-43e5]]"
title: "Hermes Agent v0.22.0 — The Threshold Release"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.0
source: hermes-agent-releases
published_at: 2026-10-14T15:23:13+00:00
fetched_at: 2026-10-18T03:19:47.130347+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent（NousResearch）於 2026-10-13 發布 v0.22.0「The Threshold Release」，週期約為 v0.21.0 的 2.5 倍：約 24,200 commits、6,080 個合併 PR、2,520 位貢獻者，並整合 v0.21.1–v0.21.7 的修補版。主軸是降低上手門檻：桌面版首次啟動會進入引導式設定對話，使用免費試用模型 nous/welcome（每個 OS 使用者一次），不需 API key；Connectors 讓 agent 透過 Nous tool gateway 操作 Linear、Notion 等託管 app，並取代原本的 MCP 分頁；本機模型可一鍵安裝並維護 llama.cpp（支援 CPU、CUDA、Metal、Vulkan、ROCm），目錄含 Qwen3.8 27B、Qwen3.8 Flash Next、Qwen3.6 35B-A3B、DeepSeek V4 Flash 及任何 Hugging Face GGUF。穩定性方面，新增 SemVer 穩定發布頻道（可用 hermes update --set-channel main 切回 main）、簽章的桌面套件（Windows MSIX 含 Microsoft Store、macOS 公證版）與統一套件管理器 hermes pm。其他包括 600 個審核過的外掛目錄、Claude Fable 5.1 / Opus 5.5 / Sonnet 5.5 / Haiku 5.5、GPT-6 Astra/Sol/Luna、GPT-6.1 Sol、Gemini 4 Argon 等模型支援、瀏覽器 agent 可用 1Password/Bitwarden 登入且模型看不到密碼、可接管的 Bot Screen，以及每台機器單一 backend 與 gateway 服務所有 profile。原文在「See and steer your subagents live」處截斷，後續內容無法確定。對 Hermes 使用者與自架本機模型的開發者影響最大。"
key_points:
  - "桌面首次啟動走引導式設定對話，使用免費試用模型 nous/welcome，免 API key；可用 Settings → Run onboarding 重跑"
  - "本機模型：一鍵安裝維護 llama.cpp，依 GPU/RAM 評分並挑選可容納的最高品質版本，目錄含 Qwen3.8 27B、DeepSeek V4 Flash 等"
  - "發布面：SemVer 穩定頻道為預設、簽章 MSIX（x64/ARM64，含 Microsoft Store）與 macOS 公證版、hermes pm 統一套件管理器（更新先建新環境，通過檢查才切換）"
tags: [hermes-agent, nous-research, local-models, llama-cpp, plugin-catalog, connectors, desktop-app]
topics: [agents.frameworks, engineering.inference, product_and_org.product]
importance: 4
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.22.0 — The Threshold Release

Hermes Agent（NousResearch）於 2026-10-13 發布 v0.22.0「The Threshold Release」，週期約為 v0.21.0 的 2.5 倍：約 24,200 commits、6,080 個合併 PR、2,520 位貢獻者，並整合 v0.21.1–v0.21.7 的修補版。主軸是降低上手門檻：桌面版首次啟動會進入引導式設定對話，使用免費試用模型 nous/welcome（每個 OS 使用者一次），不需 API key；Connectors 讓 agent 透過 Nous tool gateway 操作 Linear、Notion 等託管 app，並取代原本的 MCP 分頁；本機模型可一鍵安裝並維護 llama.cpp（支援 CPU、CUDA、Metal、Vulkan、ROCm），目錄含 Qwen3.8 27B、Qwen3.8 Flash Next、Qwen3.6 35B-A3B、DeepSeek V4 Flash 及任何 Hugging Face GGUF。穩定性方面，新增 SemVer 穩定發布頻道（可用 hermes update --set-channel main 切回 main）、簽章的桌面套件（Windows MSIX 含 Microsoft Store、macOS 公證版）與統一套件管理器 hermes pm。其他包括 600 個審核過的外掛目錄、Claude Fable 5.1 / Opus 5.5 / Sonnet 5.5 / Haiku 5.5、GPT-6 Astra/Sol/Luna、GPT-6.1 Sol、Gemini 4 Argon 等模型支援、瀏覽器 agent 可用 1Password/Bitwarden 登入且模型看不到密碼、可接管的 Bot Screen，以及每台機器單一 backend 與 gateway 服務所有 profile。原文在「See and steer your subagents live」處截斷，後續內容無法確定。對 Hermes 使用者與自架本機模型的開發者影響最大。

### 重點
- 桌面首次啟動走引導式設定對話，使用免費試用模型 nous/welcome，免 API key；可用 Settings → Run onboarding 重跑
- 本機模型：一鍵安裝維護 llama.cpp，依 GPU/RAM 評分並挑選可容納的最高品質版本，目錄含 Qwen3.8 27B、DeepSeek V4 Flash 等
- 發布面：SemVer 穩定頻道為預設、簽章 MSIX（x64/ARM64，含 Microsoft Store）與 macOS 公證版、hermes pm 統一套件管理器（更新先建新環境，通過檢查才切換）

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.22.0 
 Release Date: October 13, 2026 
 Since v0.21.0: ~24,200 commits · ~6,080 merged PRs · ~15,600 files changed · ~2,045,000 insertions · ~1,140,000 deletions · ~7,180 issues closed · ~2,520 contributors 
 
 The Threshold Release. Hermes was the god of thresholds: the doorway, the crossing, the boundary stone. v0.21.0 assembled the pantheon; v0.22.0 is about getting through the door. A fresh desktop install now opens on a guided setup chat that runs on a free trial model, so a newcomer is talking to Hermes before they own an API key. Connectors carry the agent across into the apps you already use, with no account needed to start. Local models bring it home to your own hardware with a one-click llama.cpp runtime. And the threshold itself got sturdier: tested SemVer stable releases that installs follow by default, signed desktop packages (including the Microsoft Store), and one package manager underneath everything. Around that spine: a 600-plugin catalog, the Claude 5.5 / GPT-6 model wave, password-manager sign-in for the browser, a bot screen you can take over, one backend and one gateway for every profile, and a codebase a third smaller. This is the largest window Hermes has shipped, about 2.5x the v0.21.0 cycle, and it rolls up and fully documents the v0.21.1–v0.21.7 patch releases. 
 

 
 ✨ Highlights 
 
 
 A first launch that sets itself up — Open the desktop app on a computer where you have never used Hermes and it starts a short setup chat instead of a settings screen. One card at a time it asks your name, an accent color and a layout, which apps to connect, which plugins to install, then gives a quick tour and offers up to four first tasks picked for you. It runs on a free trial model ( nous/welcome , once per OS user), so it needs no key; Skip setup ends it and Settings → Run onboarding again brings it back. The agent also gained set_theme , so "make it violet, dark mode" works in any desktop chat. ( #137429 , #137522 , #137807 , #134209 , #105258 — @alt-glitch , @OutThisLife , @ethernet8023 , @rewbs ) 
 
 
 Connectors: Hermes works inside your apps — The agent can now act in hosted apps such as Linear and Notion through the Nous tool gateway: ask for an app, sign in once in your browser, and the tools are usable in the same turn. You do not need a Nous account to start; the first time you use an app, Hermes creates a free connectors-only identity. The desktop has a new Connectors page that puts hosted apps and your MCP servers in one list (it replaces the MCP tab), the same setup card appears in the TUI and CLI, and you can connect several named accounts of one app (a work and a home account) and manage them with /connectors or hermes connectors . ( #106842 , #111008 , #119074 , #135143 , #135072 , #135097 , #135151 , #135173 , #137426 — @alt-glitch , @rewbs ) 
 
 
 Local models in one click — Hermes can now run open models entirely on your machine with nothing leaving it: no account, no API key. It installs and maintains llama.cpp with the right engine for your hardware (CPU, CUDA, Metal, Vulkan or ROCm), rates every catalog model against your GPU and RAM, and picks the highest-quality build that fits. Downloads pause and resume, the server starts and stops with Hermes, and engine updates are one click. Start from Settings → Providers → Local Models on Windows, macOS and Linux, or hermes model → Local models in a terminal. The catalog includes Qwen3.8 27B, Qwen3.8 Flash Next (with its MTP speculative head), Qwen3.6 35B-A3B and DeepSeek V4 Flash, plus any GGUF from Hugging Face. ( #100667 , #101823 , #128768 , #111423 , #133111 , #134116 — @jquesnelle , @ethernet8023 ) 
 
 
 Stable release channels — Hermes now ships tested SemVer releases. Every release passes source CI, Docker, Nix, signed desktop builds and install/upgrade runs on every OS before it is published, and source installs now move from release to release by default instead of tracking every commit on main . Prefer the bleeding edge? hermes update --set-channel main , or the new channel switch in Desktop Settings → About . Moving to an older release is labelled a rollback and never happens without asking, and installer reruns keep you on the channel you chose. ( #102765 , #135847 , #135949 , #136313 , #137780 — @ethernet8023 , @KoNit-K ) 
 
 
 Signed desktop packages, the Microsoft Store, and one package manager — The desktop app is now a sealed, signed package that carries its own Python and Node and updates itself, so first launch builds nothing. Windows gets a signed MSIX (x64 and ARM64) through App Installer or the Microsoft Store; macOS gets a signed, notarized build for Apple Silicon. Underneath, a new unified package manager ( hermes pm ) owns every pinned, hash-checked tool and Python environment: updates build a new environment and switch only once it passes its check, so a failed or killed update can no longer leave you half-applied. ( #102765 , #132361 , #132386 , #120339 , #122221 — @ethernet8023 ) 
 
 
 The Plugin Catalog: 600 reviewed plugins — The plugin catalog launched this cycle and grew to 600 entries, each pinned to a reviewed commit and installable from Hermes Desktop or the CLI. Browse by category and star ranking with a page per plugin and per author; catalog rules keep listed plugins from patching Hermes internals or shipping unscannable binaries. Memory providers now live with their makers (Honcho, Supermemory, Hindsight, Mem0, OpenViking, Holographic), as do Home Assistant, Spotify and Langfuse: existing users are migrated automatically, and the default install got leaner. ( #69446 , #111415 , #117808 , #113381 , #114732 , #131267 , #132476 , #136436 — @itpartypattaya , @happy5318 , and 400+ plugin authors) 
 
 
 The Claude 5.5 and GPT-6 model wave — Claude Fable 5.1, Opus 5.5, Sonnet 5.5 and Haiku 5.5, GPT-6 Astra, Sol and Luna plus GPT-6.1 Sol, and Gemini 4 Argon are pickable on Nous Portal, OpenRouter and native routes where offered. Prior reasoning is now replayed by default on every provider that can read it, across resume, branches and compaction, so long multi-step work keeps its train of thought. And when a provider has a bad hour, Hermes waits out transient 503/529/timeouts in visible, bounded cycles instead of ending your turn. ( #100577 , #119304 , #126842 , #134759 , #128248 , #137955 , #136358 , #116353 — @kshitijk4poor , @unsupportedpastels , @100yenadmin , @mssteuer , @xxxigm ) 
 
 
 Sign in to websites with your password manager — The browser agent can log into sites with logins from 1Password, Bitwarden or Hermes's own encrypted vault, and the model never sees the password. If nothing is saved, you get a masked prompt in the CLI, TUI or Desktop to save it, one-time codes are filled without entering the conversation, and card and address fills at checkout need your confirmation. ( #106480 , #107585 , #137084 ) 
 
 
 Bot Screen: watch your bot work, take over when it needs you — A bot running on a Linux gateway can have its own desktop that Hermes Desktop streams live. When it hits a login, a 2FA prompt or a CAPTCHA, you take the screen, finish the step yourself, and hand control back while the bot carries on with your session. With a Docker, SSH or Singularity backend, the bot's screen, computer use and the browser run inside the sandbox, never on your host. ( #108914 , #121169 , #121110 ) 
 
 
 One backend and one gateway for every profile — Hermes now runs a single messaging gateway and a single desktop backend per machine that serve all of your profiles, instead of one process per profile. Creating a profile makes its bots live without a restart, each profile keeps its own credentials, allowlists, cron jobs and sessions, and hermes update migrates existing per-profile setups automatically. Fewer processes, no token clashes, one thing to start and stop. ( #112854 , #108928 , #118273 , #117983 , #118246 , #118027 ) 
 
 
 See and steer your subagents live — Running subagents now stay visible above the composer in the CLI (F6), TUI (Ctrl+T) and Desktop with each child's task, elapsed time and live transcript, plus Steer and Stop buttons. /stop reaches background children and hands back their partial work, and delegate_task can pass screenshots and mocks to vision-capable children. ( #105593 , #115616 , #97689 ) 
 
 
 A model picker that knows your plans — Star your favorite models, see a subscription running low ("17% left · resets 3:00 PM") and when a rate limit lifts right in the picker, and pick reasoning effort as part of choosing a model in hermes model , /model ( /model X --reasoning high ) and Desktop. You switch before you hit the wall instead of after. ( #126535 , #133392 , #133408 , #110346 , #113117 — @OutThisLife , @anotherchu ) 
 
 
 Hermes in your language, everywhere — Every user-facing string in the CLI, messaging gateway, TUI and Desktop now goes through one translation catalog with full coverage in all 16 bundled languages. New languages can ship as plugins, and any profile can override individual strings with a small YAML file. ( #126296 ) 
 
 
 Leaner in every sense — The whole codebase was simplified with zero behavior change: source went from about 1.06M to 698K lines (−34%) and gateway/run.py shrank from 34,847 lines to 5,512. Prompts got lighter too: about 19 rarely used tools now load only when the agent searches for them, roughly halving the desktop tool schema sent on every call, and another ~2.1k tokens came off the fixed prompt. Local models prefill less on every turn. ( #102117 , #97979 , #106676 , #137084 — @alt-glitch ) 
 
 
 Small comforts that add up — Opt-in vim keys in the CLI prompt, a git-branch field in the status bar, a bell and desktop notification when Hermes is waiting on you, Ctrl+C that clears your draft instead of killing the turn, an editable /queue , and hermes --native to let your own terminal handle TUI scrollback and search. On Desktop, a new Simple mode turns the app into a plain chat window, and errors now say what went wrong with a one-click fix. ( #106412 , #106434 , #101284 , #101320 , #137065 , #95999 , #121035 , #118587 , #111601 — @saforem2 , @TurgutKural , @glitchbunny0 , @harshmoney123 , @pierrenode , @abhinav11082001-stack , @OutThisLife ) 
 
 
 
 ⚠️ Upgrade notes 
 
 Python 3.14 is the runtime for managed installs (the package manager installs it for you). KittenTTS is unavailable on 3.14. ( #102765 ) 
 Windows desktop is MSIX-only and needs Windows 11 22H2 or newer; the NSIS/MSI installers are gone. The macOS app is Apple Silicon only in default builds. ( #102765 , #136603 ) 
 One gateway per machine is the default. hermes update folds per-profile gateways into the multiplexed default when nothing conflicts. ( #112854 ) 
 Chats no longer reset on an idle/daily timer. session_reset idle/daily modes are retired (configs that still set them log a warning); /new or /reset starts fresh. ( #105021 , #126244 ) 
 Old sessions are pruned automatically. sessions.auto_prune now defaults to on: ended sessions inactive for 90 days are deleted at startup. Pinned and open sessions are never touched; set sessions.auto_prune: false to keep everything. 
 Memory providers moved to catalog plugins (Honcho, Supermemory, Hindsight, Mem0, OpenViking, Holographic), as did Home Assistant, Spotify and Langfuse. Existing users are migrated on update or first start, with data intact. ByteRover and RetainDB remain bundled. 
 Plugin authors: the old plugin compatibility import layer is gone ( #126164 ), hermes sync (Skill Sync) was removed ( #132465 ), and the bundled tirith scanner was removed ( #133832 ). Several tools were renamed ( todo → todo_list , cronjob → cronjob_manage , process → process_manage ); the old names still work. ( #97979 ) 
 
 
 🚪 Onboarding, Free Tier, Connectors &amp; Local Models 
 First-run onboarding 
 
 Guided setup chat on a fresh desktop install (see Highlights) . Existing installs and remote (SSH, URL, Cloud) backends don't get it automatically; the old setup-profile flow and

[... truncated for safety ...]

</details>