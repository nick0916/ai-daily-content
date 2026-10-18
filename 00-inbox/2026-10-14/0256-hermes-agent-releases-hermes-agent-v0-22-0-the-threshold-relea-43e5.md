---
id: inbox_82ada736
source: hermes-agent-releases
source_type: rss
url: "https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.0"
author: "teknium1"
published_at: 2026-10-14T15:23:13+00:00
fetched_at: 2026-10-18T02:56:52.537361+00:00
content_hash: "43e5319f22bf724eeb873f23bd6d52e0363b8aa5ccfa8bb89e0d654b25836348"
lang: en
caption_quality: None
raw: true
topics: []
---

# Hermes Agent v0.22.0 — The Threshold Release

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