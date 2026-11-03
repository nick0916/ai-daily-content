---
id: inbox_10d1f1e3
date: 2026-11-03
source_ref: "[[00-inbox/2026-11-03/2348-superpowers-releases-v7-0-2-04fa]]"
title: "v7.0.2"
url: https://github.com/obra/superpowers/releases/tag/v7.0.2
source: superpowers-releases
published_at: 2026-11-03T22:17:54+00:00
fetched_at: 2026-11-03T23:57:13.837074+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 只在答案會改變產出時才提問，其餘自行決定並說明。 **Why** 舊版 brainstorming 問題過多（盲測中填充問題由 41 降到 23），且有對話在核准前就開始建置。 **How** 無既有資訊可推定且會改變建置內容時才提問；有選項時列出並附建議，並先呈現簡短設計請使用者核准。 **What** Superpowers v7.0.2 調校 brainstorming，並修正六個 harness 的 bootstrap，包括 Copilot on Windows 的 PowerShell 錯誤、Pi 的 prompt cache 問題（@sjawhar 量測 83% 轉換會重寫快取），以及 SDD 與 executing-plans helper 新增 -C DIR 參數。"
key_points:
  - "brainstorming 在盲測中把填充問題由 41 降到 23，33/33 對話先問動機（舊版 28/33）"
  - "衝突選項情境中，由 8/8 次直接問「哪一個？」改為列出選項並推薦"
  - "Pi 每次 prompt 都注入 bootstrap，避免 Anthropic prompt cache 因首則訊息改變而重寫"
tags: [superpowers, brainstorming, prompt-caching, agent-skills, bootstrap]
topics: [agents.coding_agents, engineering.inference]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## v7.0.2

讓 AI 只在答案會改變產出時才提問，其餘自行決定並說明。

**Why** 舊版 brainstorming 問題過多（盲測中填充問題由 41 降到 23），且有對話在核准前就開始建置。

**How** 無既有資訊可推定且會改變建置內容時才提問；有選項時列出並附建議，並先呈現簡短設計請使用者核准。

**What** Superpowers v7.0.2 調校 brainstorming，並修正六個 harness 的 bootstrap，包括 Copilot on Windows 的 PowerShell 錯誤、Pi 的 prompt cache 問題（@sjawhar 量測 83% 轉換會重寫快取），以及 SDD 與 executing-plans helper 新增 -C DIR 參數。

### 重點
- brainstorming 在盲測中把填充問題由 41 降到 23，33/33 對話先問動機（舊版 28/33）
- 衝突選項情境中，由 8/8 次直接問「哪一個？」改為列出選項並推薦
- Pi 每次 prompt 都注入 bootstrap，避免 Anthropic prompt cache 因首則訊息改變而重寫

**原文：** [superpowers-releases](https://github.com/obra/superpowers/releases/tag/v7.0.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This release further tunes brainstorming's questions. It asks fewer of them, starts by asking why, and when there's a choice to make it gives you options to pick from. It also fixes bootstrap problems on six harnesses, and makes the SDD and executing-plans helper scripts much harder to point at the wrong repository or the wrong task. 
 Brainstorming 
 
 It asks a question only when the answer would change what gets built and nothing already answers it. Otherwise it states its call as a proposal you can correct. It also stops asking about process: writing things up, where files go, whether to look further, and how to show you something are its own calls, and it tells you what it decided. ( #2644 ) 
 When you haven't said why you want something, that's the first thing it asks. It asks openly, with no example answers to pick from. ( #2644 ) 
 When there's a choice it can name, it shows you the options with a recommendation. In one of our test scenarios, where a spec gives Ctrl+K to two features, 7.0.1 found the conflict every time but asked a bare "which one?" in 8 of 8 runs. This release laid out the options and recommended one in 8 of 8. ( #2644 ) 
 It reads from how you talk whether you want to discuss the technical choices, and when your request leaves nothing open, its first message is a short design for you to approve. ( #2644 ) 
 In blind-graded test conversations, filler questions dropped from 41 with 7.0.1 to 23, the reason behind the request came out before any approach in 33 of 33 conversations (28 of 33 before), and nothing got built before approval (4 times before). Against 6.4.2's brainstorming in the same scenarios, it had fewer filler questions (23 against 34), drew out the why far more often (33 of 33 against 19 of 33), and matched it at building nothing before approval. ( #2644 ) 
 start-server.sh --project-dir . now works. The script cd s into its own directory before starting the server, so every path it derived from a relative --project-dir pointed to the wrong place, and the server never started. It now resolves the directory first. Thanks @anchore-jesset for the report. ( #2524 , #2608 ) 
 
 Thanks to @mbcrawfo and everyone on #2530 who sent transcripts and tested 7.0.1. If brainstorming still asks you something it shouldn't, please tell us there, with what you asked and what it asked back. 
 Hooks 
 
 Copilot on Windows now gets the bootstrap. Copilot CLI and VS Code Copilot run hook commands through PowerShell, which rejected the SessionStart command with a ParserError. hooks.json now has a powershell form of the command. Thanks @ronpieper-engcp and @orty for the reports. ( #2189 , #1225 , #2592 ) 
 The SessionStart hook starts no child processes. On Git Bash, each one costs tens of milliseconds, and the hook started six of them on every startup, /clear and compaction. Thanks @midirectiekade14-debug for the report and measurements. ( #2081 , #2593 ) 
 On a Unix system without bash, run-hook.cmd falls back to zsh, or exits quietly. It used to exit 127 with bash: not found , and the bootstrap was lost. ( #2503 , #2594 ) 
 
 Pi 
 
 Every prompt now gets the bootstrap. The extension turned the bootstrap off after the first prompt of a session, so every later prompt went without it. Because the first message of the request changed, Anthropic prompt caching also rewrote the whole conversation's cache on the second prompt. Over a day of sessions, @sjawhar measured 83% of first-to-second-prompt transitions rewriting the cache. Thanks @DKnight927 for the report. ( #2083 , #2595 ) 
 The skills filter on the Superpowers package entry works. The extension re-added the whole skills/ directory after pi applied the filter, so "skills": [] still loaded all 15 skills. Thanks @adrian-85 for the report and @m2dumpling for the fix. ( #2394 , #2402 , #2598 ) 
 
 Hermes Agent 
 
 delegate_task subagents no longer get the controller's bootstrap. Every child started with an empty history, so each one looked like a new session and got the full bootstrap, and some started by loading using-superpowers instead of doing their task. Thanks @thealps01-netizen for the report. ( #2536 , #2596 ) 
 
 OpenCode 
 
 The bootstrap tells the model to use bare skill ids. OpenCode registers skills as brainstorming , not superpowers:brainstorming , so a model that copied the namespaced form from the bootstrap got "skill not found" and went on without the skill. Thanks @shiluoluo16 for the report. ( #2583 , #2597 ) 
 A prompt that mentions EXTREMELY_IMPORTANT no longer turns the bootstrap off. The plugin decided the bootstrap was already there if the first message contained that word, so asking "is there an EXTREMELY_IMPORTANT block in your context?" was enough to drop it. It now looks for the bootstrap's own first line. Thanks @Swift22 for the report. ( #2197 , #2600 ) 
 OpenCode 2's compaction and generate requests carry the bootstrap. Without it, the compaction request, the largest of the session, missed the prompt cache. Thanks @tpischke for the report and measurements. ( #2391 , #2601 ) 
 
 Muse 
 
 The SessionStart hook now runs on Debian and Ubuntu. Muse's manifest ran hooks/session-start , a bash script, with sh . Where sh is dash, the hook failed with exit 2 and the bootstrap never loaded. It now runs with bash . Thanks @rahul05ranjan for the report and @twotnguyen for the fix. ( #2528 , #2533 ) 
 
 Subagent-Driven Development and Executing Plans 
 
 The helpers act on the repository of the current directory, as git does, and take -C DIR to point at another. Outside a repository, sdd-workspace used to write its workspace into whatever directory the agent was in, often the plugin cache. All five helpers now stop with exit 2 and a message that tells your agent what to do. In a new project with no commits yet, your agent will need to run git init and make a first commit before it can start. -C also lets a controller review a worktree without a cd ... ; prefix that Claude Code can't allowlist. Thanks @abat-kek , @rz1989s , and @jiyimeta for the reports. ( #2429 , #2242 , #1799 , #2606 ) 
 The skills say to run the helpers by absolute path from your working tree. They used to say "from this skill's directory", and agents that cd 'd there ran the helpers against the plugin's own files. A test now fails if a skill names a helper by a relative path. Thanks @anchore-jesset for the report. ( #2525 , #2607 ) 
 task-brief finds tasks with IDs like A1 , 6b , and 2.1 . It used to reject letter-first IDs entirely, and asking for Task 6 also picked up Task 6b. When a plan's task headings aren't in English, it now says they must use the word "Task" and shows the headings it found. Thanks @rhuthik , @jnrod03-rgb , @christopherpconway , and @ferrous26 for the reports. ( #2459 , #2496 , #2175 , #2405 , #2604 ) 
 task-brief refuses a brief that an unclosed code fence ran to the end of the plan. One missing closing fence hid every later task heading, and the reporter's 177-line task came back as a 1,159-line brief holding five tasks. Thanks @bobbykim89 for the report. ( #2436 , #2605 ) 
 On Windows, the helpers print paths PowerShell can open. They printed /c/Users/... , which PowerShell reads as C:\c\Users\... . Thanks @sean-parent for the report. ( #2307 , #2602 ) 
 
 Systematic Debugging 
 
 The skill no longer installs its own test scenarios. CREATION-LOG.md and four pressure-test prompts, which open with "This is a real scenario. You must choose and act", installed next to SKILL.md and could be found by an agent mid-task. They now live under tests/ , and a test keeps files like these out of every skill. Thanks @Caarles00 for the report. ( #2277 , #2654 ) 
 
 Maintenance 
 
 scripts/package-codex-plugin.sh and scripts/sync-to-codex-plugin.sh work from a linked git worktree. ( #2609 )

</details>