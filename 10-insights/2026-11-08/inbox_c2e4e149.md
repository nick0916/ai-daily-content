---
id: inbox_c2e4e149
date: 2026-11-08
source_ref: "[[00-inbox/2026-11-08/0149-github-trending-agent-tools-ranxianglei-billion-context-4-630-191-789e]]"
title: "ranxianglei/billion-context ⭐ 4,630(今日 +191)"
url: https://github.com/ranxianglei/billion-context
source: github-trending-agent-tools
published_at: 2026-11-08T01:49:57.212646+00:00
fetched_at: 2026-11-08T01:56:52.042919+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用代理層壓縮對話上下文，讓單一長會話可跑到數十億 token。 **Why** 長程式開發的上下文會快速膨脹，按 token 計費，超出視窗後會退化或失效。 **How** 插件位於 agent 與模型 API 之間，改寫 Anthropic/OpenAI 串流；模型透過注入的工具自行決定壓縮時機與範圍，產生可還原的分層摘要，並保持 prefix cache 有效。 **What** 專案自述 4.5 個月、三台主機、174,327 次模型呼叫、最長會話 12,049 次呼叫，並宣稱約省 5 倍 token；健康會話的 cache 命中率約 95–97%，壓縮成本 ≤2%。數據為作者自述，非獨立驗證。"
key_points:
  - "代理層介入 Anthropic 與 OpenAI 串流，注入四個 context 管理工具，壓縮在 proxy 端執行，被折疊的範圍保留在歷史中直到還原。"
  - "壓縮採增量、可按需解壓的分層摘要，設計上保持 prefix cache 不失效；README 指健康會話 cache 命中率 95–97%，壓縮本身成本 ≤2%。"
  - "支援 pi、opencode、Claude、Codex 等客戶端，提供原生插件、啟動器與 URL 改寫三種用法，以 MIT 授權開源。"
tags: [context-compression, token-optimization, long-session, prefix-cache, llm-proxy]
topics: [engineering.inference, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## ranxianglei/billion-context ⭐ 4,630(今日 +191)

用代理層壓縮對話上下文，讓單一長會話可跑到數十億 token。

**Why** 長程式開發的上下文會快速膨脹，按 token 計費，超出視窗後會退化或失效。

**How** 插件位於 agent 與模型 API 之間，改寫 Anthropic/OpenAI 串流；模型透過注入的工具自行決定壓縮時機與範圍，產生可還原的分層摘要，並保持 prefix cache 有效。

**What** 專案自述 4.5 個月、三台主機、174,327 次模型呼叫、最長會話 12,049 次呼叫，並宣稱約省 5 倍 token；健康會話的 cache 命中率約 95–97%，壓縮成本 ≤2%。數據為作者自述，非獨立驗證。

### 重點
- 代理層介入 Anthropic 與 OpenAI 串流，注入四個 context 管理工具，壓縮在 proxy 端執行，被折疊的範圍保留在歷史中直到還原。
- 壓縮採增量、可按需解壓的分層摘要，設計上保持 prefix cache 不失效；README 指健康會話 cache 命中率 95–97%，壓縮本身成本 ≤2%。
- 支援 pi、opencode、Claude、Codex 等客戶端，提供原生插件、啟動器與 URL 改寫三種用法，以 MIT 授權開源。

**原文：** [github-trending-agent-tools](https://github.com/ranxianglei/billion-context)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A context-compression plugin for month-long single sessions (billions of tokens) ,small context windows (a 100K context is enough) and token savings (5x fewer tokens) .上下文压缩插件,月级长会话会话, 兼顾小窗口(100k上下文足矣)省token(省5倍token) . billion-context is all you need

billion-context

Community

📄 Paper / Preprint

Why

How it works

Which do I need?

Install

Quickstart

From source (development)

FAQ

Running the proxy

Configuration

How sessions work

Status

Attribution requirement (one term on top of MIT)

License

📊 Independent Third-Party Benchmarks

Context-management tools

Option 1 — Native plugin ( bili plugin install pi / omp / opencode / dsh / kimi / hermes / zcode )

Option 2 — Launcher ( bili pi / bili codex / bili claude / bili omp / bili opencode / bili hermes / bili dsh / bili codebuddy / bili qoder / bili trae / bili jcode / bili kimi / bili gemini / bili iflow / bili qwen / bili antigravity / bili mcode / bili aider / bili copilot / bili amp / bili goose / bili kiro )

Option 3 — URL change ( /bili/ prefix)

Client deep dives

Running in Docker

Flags

Remote agents ( --host )

Debugging

Log file

Connection lifecycle tuning (#1982)

Self-update

Stale local DNS after a network/VPN change (#5224)

Critical-defect advisories (forced updates)

Config file

Pi built-in subagents

Derived (child) sessions inherit the parent's compressed context (#1333, #1362)

Running multiple instances (#3633)

Session file cleanup (#1082)

Storage maintenance CLI (#3928)

English | 中文

Context-compression plugin — billion-context is all you need.

small context windows (100K is enough) · 5× fewer tokens · month-long single sessions (billions of tokens) · high compression quality

 

 npm install -g billion-context --prefix=~/.local 

 

Cache health at a glance: a healthy session keeps a 95–97% prefix-cache hit rate — compression itself costs ≤2%. Sustained lower? Check attribution with /acp or /acp-cache (see FAQ ); usual causes, in order: upstream cache TTL expiry · model switch · a bili bug (please report) · other/unknown.

QQ Group:
1056132097 (full)
1108730198 (full)
1129868472 (open)

📝 The paper itself is open-sourced under the MIT License as part of the codebase ( paper/ ). It is a living document — anyone may edit it; improvements are welcome via pull request.

A production-scale longitudinal study: 4.5 months, three hosts, 174,327 model calls, 18.76B cumulative input tokens (~24.7B across all hosts), zero window violations on 204,800-token models, marathon sessions of 8,584–12,049 calls.

billion-context sits between any agent and its model API, rewriting Anthropic/OpenAI streams with acp-kernel compression. The model decides when and what to compress into high-fidelity summaries — not a hard truncation limit.

Long coding sessions blow up context. Each provider charges per token, and once you pass the context window the session degrades or dies. billion-context compresses consumed conversation into layered summaries so you can run a single session for days — billions of tokens through one context window.

Unlike a host's built-in summarizer, compression here is incremental, reversible, and prefix-cache friendly : summaries are written in small ranges, can be decompressed on demand, and the cache prefix stays intact.

The proxy injects four context-management tools into the conversation; the model calls them itself as context grows, and the proxy executes compress server-side so folded ranges stay summarized in history until restored:

Pick by your client:

Native mode vs standalone extensions. The host-native plugins ( bili plugin install ... ) and the standalone in-process extensions ( billion-context-pi , opencode-acp ) are mutually exclusive — both active means double compression. The installer makes the switch: it replaces the legacy entries (bare name, npm: alias, versioned, path form; array or object shape) and snapshots the original config to .bili-bak once; a project-local install is not touched — remove that one by hand. As a runtime safety net for manual installs, the native entries set BILLION_CONTEXT_NATIVE= synchronously at load so a standalone extension can stand down at action time. On the pi side the marker needs billion-context-pi 0.1.72+ , and the pi-native entry scans both pi settings files once its proxy is up and warns loudly when it spots a co-resident legacy entry the installer never saw — that warning is the only visible signal while an old billion-context-pi silently double-compresses.

Linux / macOS — install with a user-level prefix (no sudo , no npm config
changes, and bili 's self-update never hits permission errors):

The bili command lands in ~/.local/bin — already on PATH in most distros;
if not, add export PATH="$HOME/.local/bin:$PATH" to ~/.bashrc or ~/.zshrc . On nvm or Homebrew Node the default prefix is already user-owned —
a plain npm install -g billion-context works as-is. On Windows the default
prefix ( %APPDATA%\npm ) is also user-writable — plain npm install -g billion-context .

This installs the bili command ( bili-proxy is kept as an alias). Hitting EACCES with an old root-owned prefix? Reinstall with --prefix=~/.local (pass the flag again on any future npm reinstall of bili ) — that is the
permanent fix; avoid sudo .

Prefer containers? A Dockerfile ships at the repository root — see Running in Docker below.

Three ways to use it — pick one:

Mechanism details behind these three options (plugin lifecycle, runtime-info
protocol, injection priority) live in TECHNICAL-NOTES.md .

Ports, briefly (#1660): bili start (manual) owns 8787 . Everything a lane
spawns for you (native hooks, launcher lanes) lives in a separate
self-managed zone starting at 18787 — collisions hop +1 and each lane
remembers its drift, so zero-config installs never fight you for a port,
and a deliberate bili start daemon is attached by default. Attach is
lane-aware (#2905): a hook rides its own lane's instance first, NEVER
another declared lane's — except lanes you list in native.attachLanePriority — and the 8787 user-zone daemon stays the
LAST-resort fallback. An
upgrade-restart that finds the previous build still draining on the lane's
port waits for it to release (up to 5s) and rebinds the SAM

</details>