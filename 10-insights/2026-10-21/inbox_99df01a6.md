---
id: inbox_99df01a6
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-superpowers-releases-v7-0-1-7e6f]]"
title: "v7.0.1"
url: https://github.com/obra/superpowers/releases/tag/v7.0.1
source: superpowers-releases
published_at: 2026-10-21T21:05:11+00:00
fetched_at: 2026-10-21T23:47:04.683039+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把過長的 skill 拆成參考文件，避免 Claude Code 壓縮對話後遺失內容。 **Why** Claude Code 壓縮後會重新附上每個 skill，但超過 20,000 字元的部分會被截掉，整個 session 都無法取得。 **How** 將 subagent-driven-development、writing-skills、executing-plans 的細節移到 references/，需要時才從磁碟讀取，並以測試腳本強制 SKILL.md 低於 20,000 bytes。 **What** superpowers v7.0.1 同時重調 brainstorming：先讀專案脈絡再提問，設計文件獲核准前不建置；測試情境中未寫設計文件的比例由 24/24 降為 3/24。另在 issue 與 PR 模板加入人工撰寫的摘要要求。"
key_points:
  - "超過 20,000 字元的 skill 在壓縮後會被截斷；subagent-driven-development 因此遺失五輪限制，跑了 18 輪修正（回報案例）"
  - "subagent-driven-development、writing-skills、executing-plans 拆分或精簡，test-skill-size.sh 在 SKILL.md 達 20,000 bytes 時失敗"
  - "brainstorming 改為先讀專案脈絡再提問，只在被主動要求時不再提議跳過提問；未寫設計文件的情況由 24/24 降為 3/24（測試情境）"
tags: [claude-code, skills, context-compaction, brainstorming, superpowers]
topics: [agents.coding_agents, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v7.0.1

把過長的 skill 拆成參考文件，避免 Claude Code 壓縮對話後遺失內容。

**Why** Claude Code 壓縮後會重新附上每個 skill，但超過 20,000 字元的部分會被截掉，整個 session 都無法取得。

**How** 將 subagent-driven-development、writing-skills、executing-plans 的細節移到 references/，需要時才從磁碟讀取，並以測試腳本強制 SKILL.md 低於 20,000 bytes。

**What** superpowers v7.0.1 同時重調 brainstorming：先讀專案脈絡再提問，設計文件獲核准前不建置；測試情境中未寫設計文件的比例由 24/24 降為 3/24。另在 issue 與 PR 模板加入人工撰寫的摘要要求。

### 重點
- 超過 20,000 字元的 skill 在壓縮後會被截斷；subagent-driven-development 因此遺失五輪限制，跑了 18 輪修正（回報案例）
- subagent-driven-development、writing-skills、executing-plans 拆分或精簡，test-skill-size.sh 在 SKILL.md 達 20,000 bytes 時失敗
- brainstorming 改為先讀專案脈絡再提問，只在被主動要求時不再提議跳過提問；未寫設計文件的情況由 24/24 降為 3/24（測試情境）

**原文：** [superpowers-releases](https://github.com/obra/superpowers/releases/tag/v7.0.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This release retunes brainstorming after its rebuild in v7.0.0. Many of you told us, rightly, that the new default questions got annoying fast and felt formulaic. Brainstorming now digs for context before it asks anything, and tries to ask better questions. We expect to keep tuning it, but we think it's better than it was. 
 It also trims three long skills so they better survive compaction on Claude Code, and changes the issue and PR templates to ask for a summary written by a human. 
 Brainstorming 
 
 It digs for context first. In an existing project, or when you point it at a spec, plan, or files, it reads them before its first message and doesn't ask what they already answer. ( #2560 ) 
 It tries to ask better questions. v7.0.0 opened every session the same way: an offer to skip the questions, then a generic question about "the moment you wished this existed." Now, when you've already said what you want, it plays your request back with what it found in the project and asks about the one thing still open. Later questions build on your answers and on what it found, and say what the answer would change. ( #2560 , #2571 ) 
 It offers to skip the questions only when it started on its own. If you asked for brainstorming by name or with /brainstorming , it no longer offers to skip it. ( #2560 ) 
 It lays out the approaches and writes a design doc before building. It presents two or three ways to build the thing, recommends one, and asks you to pick. Then it writes a design doc, a short one for a small change, and builds nothing until you approve it. Some of you saw it skip the doc and start building; in one of our test scenarios, it skipped the doc without asking in 24 of 24 runs before this change and 3 of 24 after. ( #2571 ) 
 
 Thanks to @mbcrawfo for opening #2530 , and to @katyatitkova , @ertra , @blorenz , @Biomaj , @fsalum , @technicalpickles , @orochi235 , @alexxburg , @fcavalieri , @CelesteCunha , and @zzzzz9999 for the reports, transcripts, and testing there. 
 If brainstorming's questions in 7.0.1 still don't feel right, please comment on #2530 . Examples help most: what you asked, what it asked back, and what you wish it had asked. 
 Skills better survive compaction on Claude Code 
 After a compaction, Claude Code re-attaches each skill cut off at 20,000 characters, so anything past that point is gone for the rest of the session. In one reported session, subagent-driven development lost its five-round limit and ran 18 fix rounds on one task. Thanks @dan-1492 for the report. ( #2481 ) 
 
 subagent-driven-development moves the fix loop, final review, report handling, resuming, preflight, batching, and cannot-verify guidance into references/ . It reads each file from disk at the step that needs it. ( #2565 ) 
 writing-skills moves its supporting docs, the SKILL.md template and discovery guidance, bulletproofing, and flowchart conventions into references/ . ( #2564 ) 
 executing-plans drops its Example Workflow, which repeated rules stated above it. ( #2563 ) 
 tests/skill-size/test-skill-size.sh fails when any SKILL.md reaches 20,000 bytes. ( #2565 ) 
 
 Contributing 
 
 Issue and PR templates now ask who is filing and what their human partner asked for, plus a summary of under 200 words written by a human. The bug report also asks how you confirmed the problem doesn't happen without Superpowers. ( #2569 ) 
 We don't accept agent-written PRs that fix someone else's issue unless a maintainer asked for one. If your human partner hit the same problem, add their report to the existing issue. The PR template, AGENTS.md , and the README say so. ( #2569 ) 
 diagnosing-superpowers adds the same two sections to the issues it drafts and won't file one while the summary is a placeholder. Its prefilled link now opens the Bug Report template; we removed the Session Diagnosis Report template. ( #2569 )

</details>