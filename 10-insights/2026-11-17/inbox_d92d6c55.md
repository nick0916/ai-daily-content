---
id: inbox_d92d6c55
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2318-github-trending-agent-tools-elementalsouls-claude-bughunter-9-176-1-7e3a]]"
title: "elementalsouls/Claude-BugHunter ⭐ 9,176(今日 +1,007)"
url: https://github.com/elementalsouls/Claude-BugHunter
source: github-trending-agent-tools
published_at: 2026-11-17T23:18:24.242549+00:00
fetched_at: 2026-11-17T23:29:56.396427+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Claude Code 具備漏洞獵人與紅隊工作的專業技能包，依主題自動觸發。 **Why** 外部攻擊面的 bug bounty 與授權測試需要大量領域知識與流程紀律。 **How** 以 Agent Skills 格式（SKILL.md）打包，涵蓋 6 階段流程（recon、map & rank、hunt、validate、report），並有 7 題送件前檢查閘門，其中包含 scope 確認。 **What** 作者 Sachin Sharma 提供 83 個 skills（開頭描述寫 82）、15 個 slash commands、681 份披露報告模式，涵蓋 24 類核心漏洞；限定授權標的，不涵蓋內網 AD 攻擊鏈。"
key_points:
  - "83 個 skills 依主題自動載入（原文開頭寫 82，內文多處寫 83，數字不一致）"
  - "6 階段非線性流程，以程式碼強制 scope，送件前需通過 7 題 Gate"
  - "明確排除 0-day 武器化、後滲透工具、惡意程式開發；內網 AD 與 post-exploit 不在範圍內"
tags: [claude-code, bug-bounty, red-team, agent-skills, security-research]
topics: [security, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## elementalsouls/Claude-BugHunter ⭐ 9,176(今日 +1,007)

讓 Claude Code 具備漏洞獵人與紅隊工作的專業技能包，依主題自動觸發。

**Why** 外部攻擊面的 bug bounty 與授權測試需要大量領域知識與流程紀律。

**How** 以 Agent Skills 格式（SKILL.md）打包，涵蓋 6 階段流程（recon、map & rank、hunt、validate、report），並有 7 題送件前檢查閘門，其中包含 scope 確認。

**What** 作者 Sachin Sharma 提供 83 個 skills（開頭描述寫 82）、15 個 slash commands、681 份披露報告模式，涵蓋 24 類核心漏洞；限定授權標的，不涵蓋內網 AD 攻擊鏈。

### 重點
- 83 個 skills 依主題自動載入（原文開頭寫 82，內文多處寫 83，數字不一致）
- 6 階段非線性流程，以程式碼強制 scope，送件前需通過 7 題 Gate
- 明確排除 0-day 武器化、後滲透工具、惡意程式開發；內網 AD 與 post-exploit 不在範圍內

**原文：** [github-trending-agent-tools](https://github.com/elementalsouls/Claude-BugHunter)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A Claude Code skill bundle for bug hunting and external red-team work - 82 skills, 15 slash commands, 681 disclosed-report patterns curated across 24 core vulnerability classes, plus enterprise identity + infrastructure attack matrices.

claude-bughunter

What is this?

Quickstart

Runs on multiple agent harnesses

Star History

Scope — what this bundle is for, and what it isn't

What's inside

How it works

Authorization

Documentation

Why this exists

Roadmap

Sponsors

About

License

In scope

Out of scope (deliberate — not gaps, design decisions)

Why your model switched mid-session

A self-contained Claude skill bundle for bug hunting and external red-team work · 83 skills · 15 slash commands · 681 disclosed-report patterns (433 now individually cited & auditable) across 24 core vulnerability classes · enterprise identity + infrastructure attack matrices · engagement-folder scaffolding · Burp MCP integration · battle-tested across authorized red-team and bug-hunting engagements, plus public training platforms (DVWA, OWASP Juice Shop, Hacker101, testphp.vulnweb.com).

Built by Sachin Sharma — Bug Hunting & GenAI Security Research.

 SPONSORED BY 

claude-bughunter is a drop-in skill bundle for the Claude Code skills system . Install once and Claude Code stops being a chatbot and starts behaving like a senior bug-hunting researcher or red-team operator: it knows the techniques, the chain templates, the VRT mappings, the platform CVE chains, and the hygiene — and it stays in scope.

Four layers stack:

All triggered automatically by topic — describe what you're testing in plain English and the relevant skill loads. No invocation by name.

Option A — install as a Claude Code plugin (recommended). From inside Claude Code:

All 83 skills + 15 commands load namespaced under claude-bughunter: and update when you bump the plugin version — no files copied into ~/.claude/ .

Option B — copy install (no plugin system / pin to a clone):

Both copy the skills + commands into ~/.claude/ (macOS/Linux) or %USERPROFILE%\.claude\ (Windows) and wire the hunt engagement scaffolder.

What each install path gives you:

The plugin is the fastest path to the skills + slash commands. The terminal-native cbh runner installs standalone — pipx install git+https://github.com/elementalsouls/Claude-BugHunter — so plugin users can add it without a full clone (see cbh CLI ).
The hunt engagement scaffolder ships with the clone (Option B).

That's it. Open Claude Code and describe what you're testing in plain English — the right skill loads automatically, no invocation by name:

→ Full Installation guide · Usage guide · searchable skill catalog .

The block above is an illustrative transcript. To record a real demo of your own session: asciinema rec demo.cast → upload to asciinema.org and drop the badge here.

The skills are plain Agent Skills — the same SKILL.md format that Claude Code · OpenCode · OpenAI Codex CLI · Hermes Agent · Google AntiGravity all load. One command installs them everywhere:

--all ( -All ) detects installed harnesses and copies skills to each harness's path ( ~/.claude/skills , ~/.agents/skills , ~/.hermes/skills , ~/.gemini/config/skills ); --burp-mcp ( -BurpMcp ) wires the Burp MCP server into each. The full knowledge layer ports to all five — the slash commands and /hunt engine stay Claude-Code-only by design.

→ Multi-harness guide

Chart is self-hosted — regenerate with python3 scripts/gen_star_history.py (needs gh auth login ).
Refreshes automatically each day via .github/workflows/star-history.yml .

This bundle covers the external attack surface — anything reachable from the internet without first compromising an internal endpoint.

If you're running an internal red team that includes domain-takeover chains via Kerberos or lateral movement, this bundle won't help you in those phases — and we'd rather say that up front than have you find out mid-engagement. The external surface handoff to internal-RT tooling (Impacket, NetExec, CrackMapExec, Rubeus, Certify, BloodHound) is intentionally outside our scope. Coverage for internal AD and post-exploit may come in a future update.

83 skills , auto-loaded by topic — no invocation by name. Coverage across the external attack surface:

Full searchable catalog → docs/skills.md . Also ships 15 slash commands ( /hunt , /recon , /report , ...) and a deterministic engagement engine ( engine/ ) that maps a target's attack surface and routes each finding to the skill that handles it.

A 6-phase, non-linear workflow — recon → map & rank → hunt → validate → report — with scope enforced in code and a 7-Question Gate before anything is submitted. Two ways to drive it:

→ Usage guide & worked example · 6-phase architecture & skill-to-phase map · cbh CLI

These skills are intended for assets you own or have written authorization to assess (bug-bounty in-scope assets, pentest engagement letters, CTF challenges, your own infrastructure).

The skills include validation gates that auto-trigger when you point Claude at unverified third-party targets — triage-validation 's 7-Question Gate explicitly asks whether the asset is in scope (Q3) and on the program's accepted-impact list (Q2). The bugcrowd-reporting skill includes researcher-side hygiene (Bugcrowdninja alias, account-state restoration, friendly-tester posture) that signals legitimate authorized testing to the target's fraud team.

The bundle explicitly excludes : weaponizing 0-days against unauthorized targets, post-exploitation tooling, malware development, mass-targeting infrastructure. See SECURITY.md for the full posture.

Heads-up — Anthropic runtime cyber safeguards. Anthropic's models apply real-time safeguards that block "vulnerability exploitation or offensive security tooling development" by default — so even authorized, in-scope work can hit a refusal that isn't this bundle's doing. If you do authorized offensive security (pentest / bug bounty / red team), enroll in Anthropic's free, application-based Cyber Verification Program (CVP) to get safeguards adjusted for legitimate dual-use work. (Mass data exfiltration and ransomware development stay prohibited and are not adjustable.) Details: Anthropic — real-time cyb

</details>