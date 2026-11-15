---
id: inbox_c9b6a14b
date: 2026-11-15
source_ref: "[[00-inbox/2026-11-15/0125-github-trending-agent-tools-juliusbrussee-caveman-120-088-227-75c3]]"
title: "JuliusBrussee/caveman ⭐ 120,088(今日 +227)"
url: https://github.com/JuliusBrussee/caveman
source: github-trending-agent-tools
published_at: 2026-11-15T01:25:51.811535+00:00
fetched_at: 2026-11-15T01:32:25.135019+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "以極簡口吻（自稱 caveman）縮減 AI 代理輸出與讀取 token 的開源工具。 **Why** 代理的回答與讀取的內容消耗大量 token，直接影響成本。 **How** 以精簡語氣規則減少輸出，並以代理層壓縮讀入內容；原文引用 Adobe 研究指出壓縮 prompt 會降低回答品質，因此不改動 prompt。 **What** GitHub 星數約 120,088（今日 +227）；官方宣稱可減少約 65% token，Auto 模式成本為 Opus 5.5 xhigh 的 0.46 倍，數據皆為作者自測。"
key_points:
  - "官方宣稱輸入 token 減少 33.2%，Auto 模式成本為 0.46 倍；樣本為 85 個 SWE 任務，分數差 0.5 點，作者自承樣本有限"
  - "壓縮 prompt 會降低回答品質，因此工具只壓縮代理的輸出與讀取內容"
  - "支援 Claude Code、OpenCode、Codex、Gemini CLI 等 30+ 工具；4.0 版含六個可獨立開關的模組"
tags: [token-cost, coding-agents, claude-code, output-compression, open-source-tool]
topics: [agents.coding_agents, engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## JuliusBrussee/caveman ⭐ 120,088(今日 +227)

以極簡口吻（自稱 caveman）縮減 AI 代理輸出與讀取 token 的開源工具。

**Why** 代理的回答與讀取的內容消耗大量 token，直接影響成本。

**How** 以精簡語氣規則減少輸出，並以代理層壓縮讀入內容；原文引用 Adobe 研究指出壓縮 prompt 會降低回答品質，因此不改動 prompt。

**What** GitHub 星數約 120,088（今日 +227）；官方宣稱可減少約 65% token，Auto 模式成本為 Opus 5.5 xhigh 的 0.46 倍，數據皆為作者自測。

### 重點
- 官方宣稱輸入 token 減少 33.2%，Auto 模式成本為 0.46 倍；樣本為 85 個 SWE 任務，分數差 0.5 點，作者自承樣本有限
- 壓縮 prompt 會降低回答品質，因此工具只壓縮代理的輸出與讀取內容
- 支援 Claude Code、OpenCode、Codex、Gemini CLI 等 30+ 工具；4.0 版含六個可獨立開關的模組

**原文：** [github-trending-agent-tools](https://github.com/JuliusBrussee/caveman)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

🪨 why use many token when few token do trick. Viral skill + proxy for coding agents that cuts 65% of tokens by talking like a caveman.

why many token when few do trick

New: Caveman Code. Free.

Install

Six rocks, one install

Proof

Say less: the caveman voice

Read less: 33.2% fewer input tokens

Auto: 54% cheaper, same score

Blocks: code mode, script written once

Smaller rocks

Commands

Caveman Cloud

In the wild

Privacy

License

Cite

21% cheaper

14% cheaper

76% cheaper

33.2% fewer

54% cheaper

397 → 76

1.4 to 2.4× cheaper

The most efficient coding agent. Same model, same work, smaller bill.

Same model on both sides: GPT-6.1 Sol against Codex, Opus 5.5 against Claude Code. Our own runs, November 2026, at list prices. How we measured

Every coding agent in one window. Free on the subscriptions and keys you already have.

Download Caveman Code for Mac · Read the launch post

Caveman make your AI agent say less and read less. Code stay exact. Brain still big.

 

Cited by Adobe Research · A/B tested by JetBrains · Remade for Elasticsearch on Elasticsearch Labs #1 on Hacker News · #1 on GitHub Trending · "No way this actually works." ThePrimeagen

Install · Six rocks · Proof · Say less · Read less · Auto · Blocks · Commands · Caveman Cloud

The reason your React component is re-rendering is likely because you're creating a new object reference on each render cycle. When you pass an inline object as a prop, React's shallow comparison sees it as a different object every time, which triggers a re-render. I'd recommend using useMemo to memoize the object.

New object ref each render, so React re-renders. Wrap the prop in useMemo .

Same fix. 63 token become 20. Brain still big.

Pick your club:

Token counts: tiktoken o200k.

One command. Mac, Linux, Windows. Caveman find your agents and your logins, show what it change. Press Enter. Done. Needs Node.js 22.13+.

After that, plain claude stays caveman'd. So do Codex, Gemini CLI, OpenCode, and 30+ more . It runs on your machine, with your keys and your Claude Pro/Max login. One rock. That it.

Had caveman before 4.0? Say @latest , or the old copy on your machine wins. Already set up? caveman setup opens the screen again. Only want shorter answers? Get just the skill .

New in 4.0: caveman is six parts. All on after install. Each has its own switch.

caveman status shows what is on. caveman off browse turns one off. Only Auto needs an account, and it is free. 4.0.0 release notes

Outside labs first. Ours come with each rock below. Nothing rounded up. Red rows stay red.

Two findings shaped caveman. Adobe: cavemanning your prompt makes answers worse, so caveman never touches your prompt. JetBrains: agent sessions are mostly code and tool calls, which the voice leaves alone. So caveman grew rocks that shrink what the agent reads and what it runs on .

A voice, not broken grammar. Every reply follows the same structure.

Ten dev questions on claude-opus-5-5:

"Be concise" is the real baseline; new models already know it. On top of it, /caveman cuts 3% more at the median and /ultracave 35% more. Measured on the 3.1.0 rules, not yet re-run. The rules cost about 1,160 tokens of input, and if you pay per request (GitHub Copilot), shorter answers save nothing. Harness · Every case where caveman loses

Only want this rock? The skill alone, no proxy:

Type /caveman ( $caveman in Codex) if it doesn't start on its own. Say stop caveman to go back.

Claude on the web, the phone app, or Cowork? No terminal. Add caveman to your Claude account once, in Customize > Plugins: steps . Not tested end to end yet.

Already inside Claude Code? Same rock, slash form. Type these where you talk to Claude:

Windows, PowerShell 5.1+:

On npm 12 or newer, new npm block git install. One-liners above handle it themselves from v3.2.0 on. Old one-liner pinned to v3.1.0 or older still fail there: use one above, or this: npx --allow-git=root -y github:JuliusBrussee/caveman#v4.1.0

Changed your mind: npx -y github:JuliusBrussee/caveman -- --uninstall (on npm 12+, add --allow-git=root too)

Only grabbed the skill? npx skills remove JuliusBrussee/caveman -g take it back out.

Install broke? Open your agent in this repo and say "Read CLAUDE.md and INSTALL.md, install caveman for me." Agent fix own brain.

The voice shrinks what the agent says. This shrinks what it reads. Same answers: 18 of 18 right.

The file is each test file through today's compressor alone. The session is the whole agent run, which also carries the system prompt and tools, so it moves less. Honest part: the session run is from August 2026 on an older engine, HTML has no compressor yet so it lost, and each test file hides one record in 61 to 72 KB of noise. Yours will vary. Headroom on the same suite: 15 of 18 right, 6.7% fewer tokens. Method

Every original stays on your disk. The agent can pull it back any time.

New model in your agent's picker. Pick Auto and caveman chooses the model and the effort for each ask. Hard ask, big brain. Easy ask, save rocks.

Auto costs 0.46× what Opus 5.5 at xhigh costs. That is 54% saved, in under half the time. 85 real coding tasks from SWE-Interact and SWE-Together, one try each. Honest part: the run is half done, the 0.5-point score gap is too small to tell apart at this size (±7), and most of the saving is Auto lowering effort on easy asks. Already on Opus at medium? Expect less; not measured yet. Full table and limits

Works in Claude Code, OpenCode, and Codex on a ChatGPT login, with API keys, Claude Pro/Max, or ChatGPT. Any other model you pick runs as picked. Not signed in: no Auto, nothing sent. What Auto sends

skills.sh for code mode. Code mode is the agent writing a script instead of making tool call after tool call ( Cloudflare , Anthropic ). Problem: agent write same script every session, throw it away, write it again. Blocks keep it in your repo, check it every pull request, hand it back.

Tokens the agent reads back. In one week, agents on one machine wrote the same script 394 times . Purdue measured the habit at up to 9.57% of task cost. grep-defs loses to a bare grep; row stays

</details>