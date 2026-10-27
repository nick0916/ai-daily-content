---
id: inbox_c11bb562
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/0125-github-trending-agent-tools-nvidia-skillspector-22-224-214-4718]]"
title: "NVIDIA/SkillSpector ⭐ 22,224(今日 +214)"
url: https://github.com/NVIDIA/SkillSpector
source: github-trending-agent-tools
published_at: 2026-10-27T01:25:27.449568+00:00
fetched_at: 2026-10-27T01:38:32.587279+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "在安裝 AI agent skill 之前，先掃描其中的漏洞、惡意模式與 prompt injection。 **Why** agent skills 通常以隱含信任執行，且缺乏審查。 **How** 結合靜態分析與可選的 LLM 語意分析，涵蓋 prompt injection、資料外洩、供應鏈、YARA 與 taint tracking 等類別的規則。 **What** 原文引用研究資料集中 31,132 個 skill 的子集，其中 26.1% 含漏洞、5.2% 顯示疑似惡意意圖；工具支援 Claude Code、Codex 與 MCP skill，提供 CLI、Docker 與批次掃描。GitHub 星數約 22,224（今日 +214）。"
key_points:
  - "研究數據：31,132 個 skill 的分析子集中，26.1% 含漏洞、5.2% 疑似惡意"
  - "靜態分析規則：供應鏈 10+ 模式、prompt injection 6 種、資料外洩 4 種、YARA 4 種、taint tracking 5 種"
  - "可選 LLM 語意分析（預設 DeepSeek，README 註明其 structured output 限制），另提供 Docker 免 Python 執行、批次掃描與 MCP Registry 快照比對"
tags: [agent-security, skill-scanning, prompt-injection, supply-chain, mcp]
topics: [security, agents.mcp, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## NVIDIA/SkillSpector ⭐ 22,224(今日 +214)

在安裝 AI agent skill 之前，先掃描其中的漏洞、惡意模式與 prompt injection。

**Why** agent skills 通常以隱含信任執行，且缺乏審查。

**How** 結合靜態分析與可選的 LLM 語意分析，涵蓋 prompt injection、資料外洩、供應鏈、YARA 與 taint tracking 等類別的規則。

**What** 原文引用研究資料集中 31,132 個 skill 的子集，其中 26.1% 含漏洞、5.2% 顯示疑似惡意意圖；工具支援 Claude Code、Codex 與 MCP skill，提供 CLI、Docker 與批次掃描。GitHub 星數約 22,224（今日 +214）。

### 重點
- 研究數據：31,132 個 skill 的分析子集中，26.1% 含漏洞、5.2% 疑似惡意
- 靜態分析規則：供應鏈 10+ 模式、prompt injection 6 種、資料外洩 4 種、YARA 4 種、taint tracking 5 種
- 可選 LLM 語意分析（預設 DeepSeek，README 註明其 structured output 限制），另提供 Docker 免 Python 執行、批次掃描與 MCP Registry 快照比對

**原文：** [github-trending-agent-tools](https://github.com/NVIDIA/SkillSpector)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Security scanner for AI agent skills. Detect vulnerabilities, malicious patterns, security risks, prompt injection, data exfiltration, and supply-chain risks in Claude Code, Codex, and MCP skills before you install them.

SkillSpector

Overview

Documentation

Features

Quick Start

Vulnerability Patterns

Risk Scoring

Example Output

Configuration

Integrating SkillSpector

Development

How It Works

Live Vulnerability Lookups (SC4)

Trust model and data egress

Limitations

Research Background

Python API Integration

License

Contributing

Support

Installation

Docker (no Python required)

Basic Usage

Output Formats

Batch Scanning

Comparing MCP Registry snapshots

Suppressing False Positives (baseline)

Explicit scan scope

LLM Analysis

MCP Server

Prompt Injection (6 patterns)

Anti-Refusal (3 patterns)

Data Exfiltration (4 patterns)

Privilege Escalation (3 patterns)

Supply Chain (10+ patterns)

Excessive Agency (5 patterns)

Output Handling (3 patterns)

System Prompt Leakage (3 patterns)

Memory Poisoning (3 patterns)

Tool Misuse (3 patterns)

Rogue Agent (2 patterns)

Trigger Abuse (3 patterns)

Behavioral AST (9 patterns)

Taint Tracking (5 patterns)

YARA Signatures (4 patterns)

MCP Least Privilege (4 patterns)

MCP Tool Poisoning (4 patterns)

Score Calculation

Severity Levels

Terminal Output

Environment Variables

CLI Options

Exit codes

Machine-readable output

Recommended gate mapping

Setup

Stage 1: Static Analysis

Stage 2: LLM Semantic Analysis (Optional)

Security scanner for AI agent skills. Detect vulnerabilities, malicious patterns, and security risks before installing agent skills.

AI agent skills (used by Claude Code, Codex CLI, Gemini CLI, etc.) execute with implicit trust and minimal vetting. In the 31,132-skill analyzed subset of the research dataset, 26.1% of skills contain vulnerabilities and 5.2% show likely malicious intent .

SkillSpector helps you answer: "Is this skill safe to install?"

SkillSpector is part of the NVIDIA Verified Skills pipeline , which scans, evaluates, and signs agent skills before publication. Skills that pass are published to the NVIDIA skills catalog .

Open-source software notice: This project will download and install additional third-party open source software projects. Review the license terms of these open source projects before use.

Create and activate a virtual environment first (all make targets assume the venv is active). Use uv or pip ; the Makefile uses uv if available, otherwise pip .

Quick install with uv (CLI-only):

If you plan to run skillspector mcp , install the MCP extra at install time:

From source:

Run SkillSpector without installing Python by building it locally from the included Dockerfile . The image is based on the Docker Official Python 3.12-slim-bookworm image.

Build the image:

Scan a local directory by mounting your current directory into /scan , the container's working directory:

Scan with LLM analysis by passing credentials with a local .env file:

Or pass credentials directly from your shell environment:

Write a report to the host filesystem by writing to the mounted directory:

Optional alias for repeated static scans:

SkillSpector enforces two independent caps on remote and archive inputs to bound the impact of oversized downloads and zip bombs:

Note that the per-file 1 MB analysis cap ( MAX_FILE_BYTES ) is a separate, downstream limit: it bounds what individual analyzers will read out of an already-ingested directory. The ingest caps above bound how much content can land on disk in the first place. A breach of either ingest cap fails closed with an IngestLimitExceededError .

Scan entire directories of skills in parallel from contrib/batch_scan/ :

Supports multilingual detection (zh/ja/ko) and terminal/JSON/Markdown output.

For LLM scans with higher concurrency, configure multiple API keys following .env.example — the pool improves throughput
and resilience, provided the keys don't share an account-level rate limit.

See the contrib guide for details.

Note on LLM support: The default configuration targets DeepSeek as the
cheapest public option. DeepSeek-Chat is expected to sunset , and the contributor
does not have hardware to test against local models. The batch scanner was
originally tested with OpenAI-compatible endpoints — DeepSeek's lack of
structured-output support required manual JSON-parsing patches. If you can
contribute a more universal backend (Ollama, vLLM, or a different provider),
PRs are very welcome.

Start with raw registry payload captures ( registry-before.json and registry-after.json ). Save a scan report as previous.json , then compare a
later scan against that generated local report:

The optional comparison object lists added and removed server identities,
changed normalized fields with their previous and current values, and an unchanged_count . Identity is the server name and version, so a new version
appears as an addition and the old version as a removal if it is absent from the
new scan. Acquisition source and scan timestamp are excluded from comparison. unmodeled_changes lists same-identity records whose raw-record hash changed
while normalized fields match; these are not counted as unchanged. This can
indicate a change to fields outside the snapshot model, or array reordering in
the raw record. Package and remote ordering alone is not a normalized field change.
Entries in changed may also contain changes outside the snapshot model; inspect
the raw record to see those changes.
Compare reports with the same selection scope: a server absent from the current
input is reported as removed, which does not prove it was removed from a registry.

The comparison file must be a local report produced by this registry mode with
valid normalized snapshots. Malformed, oversized or duplicate server identities
are rejected. This option requires --mcp-registry and is separate from the
finding-suppression --baseline : it never suppresses findings or changes risk
scores, and it does not fetch or execute listed server endpoints.

Registry mode rejects skill-only controls such as --use-shipped-baseline , --transitive , --transitive-depth , --transitive-allow-prefix , and --transitiv

</details>