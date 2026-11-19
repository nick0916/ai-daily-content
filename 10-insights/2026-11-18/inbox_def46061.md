---
id: inbox_def46061
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-claude-mem-releases-v16-0-0-884f]]"
title: "v16.0.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v16.0.0
source: claude-mem-releases
published_at: 2026-11-18T03:11:11+00:00
fetched_at: 2026-11-19T08:21:23.613053+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v16.0.0 重做 My Work 介面，並移除 Observation TV 功能。 **Why** 原文說明此次改版來自完整的 UI 審查，目標是讓需要使用者處理的事項排在最前面。 **How** 首頁把最需要回覆的請求置頂，長列表預設摺疊，並讓每頁可在 390px 手機寬度下使用、支援鍵盤與螢幕閱讀器。 **What** /tv、tv.html 與 CLAUDE_MEM_TV_TOKEN 已從開源 worker 移除；若曾從其他機器看 TV，需設定 CLAUDE_MEM_LOCAL_API_TOKEN 並刪除 CLAUDE_MEM_TV_TOKEN；首頁高度由約 5,138px 降至約 2,600px。"
key_points:
  - "移除 /tv、tv.html 與 CLAUDE_MEM_TV_TOKEN；遠端存取改用 CLAUDE_MEM_LOCAL_API_TOKEN"
  - "首頁約 2,600px（原 5,138px）；List 初始 5 列（原 195 列）；My Rules 約 4,400px（原 17,000px 以上）"
  - "未設定 local API token 的 worker 會綁定 127.0.0.1 並記錄 SECURITY 錯誤"
tags: [claude-mem, release-notes, ui-redesign, breaking-change, security-token]
topics: [agents.coding_agents, security]
importance: 3
novelty: 3
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v16.0.0

claude-mem v16.0.0 重做 My Work 介面，並移除 Observation TV 功能。

**Why** 原文說明此次改版來自完整的 UI 審查，目標是讓需要使用者處理的事項排在最前面。

**How** 首頁把最需要回覆的請求置頂，長列表預設摺疊，並讓每頁可在 390px 手機寬度下使用、支援鍵盤與螢幕閱讀器。

**What** /tv、tv.html 與 CLAUDE_MEM_TV_TOKEN 已從開源 worker 移除；若曾從其他機器看 TV，需設定 CLAUDE_MEM_LOCAL_API_TOKEN 並刪除 CLAUDE_MEM_TV_TOKEN；首頁高度由約 5,138px 降至約 2,600px。

### 重點
- 移除 /tv、tv.html 與 CLAUDE_MEM_TV_TOKEN；遠端存取改用 CLAUDE_MEM_LOCAL_API_TOKEN
- 首頁約 2,600px（原 5,138px）；List 初始 5 列（原 195 列）；My Rules 約 4,400px（原 17,000px 以上）
- 未設定 local API token 的 worker 會綁定 127.0.0.1 並記錄 SECURITY 錯誤

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v16.0.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

My Work puts what needs you first 
 My Work, the page that shows what your agents are doing, was rebuilt from a full UI review ( #6210 , #6304 ). What needs you sits at the top, long lists fold, and every page works on a phone, by keyboard and with a screen reader. 
 
 What needs you comes first. On the home page the first request waiting on you is at the top, with the one orange button on the screen. Requests are one-line rows; Idle and Shipped fold to one row each, with their counts. 
 Shorter pages. On a real install: home is about 2,600px tall instead of 5,138; the List opens with 5 rows instead of 195; My Rules is about 4,400px instead of over 17,000. 
 Reply where you read. A request's drawer puts the reply box right under its progress line, in every state. While a reply is on its way, "Reply here" waits, so a message can never go to a second conversation as a second paid turn. 
 A focus area's page reads top to bottom: what needs you, the asks not started yet, then the board. A failed save says which change failed and offers Try again on that screen only. Past focus shows the day an area was marked done. 
 My Rules: one rule to decide at a time , with one orange Approve. On a phone, swipe to decide. 
 Fits a phone. Every page is 390px wide on a 390px phone, with a bottom bar for My Work, Focus and My Rules. 
 Keyboard and screen readers. Every control has a name; tooltips open from Tab; focus comes back to where you were after a dialog, the drawer, Dismiss or Try again; controls are 44px on touch. 
 Theme before load. Your light or dark choice is drawn before the first frame, loading and error screens included. 
 Plain errors. A failure is one sentence in your language, with the raw reason folded under Details. Nothing retries by itself. 
 Your language and clock. Times show in your language from the recorded time (French reads a 24-hour clock), and a day from another year shows its year. New strings are translated into French, Korean, Turkish and Chinese; corrections from native speakers are welcome. 
 Less motion. A live update moves at most two things, and nothing moves with reduced motion on. 
 
 Observation TV is removed 
 
 The TV page and its read-only remote access are gone from the open-source worker ( #6295 ): /tv , tv.html and the CLAUDE_MEM_TV_TOKEN setting. The classic viewer and My Work are unchanged. 
 If you watched TV from another machine: set CLAUDE_MEM_LOCAL_API_TOKEN , which protects network access now, and delete CLAUDE_MEM_TV_TOKEN . Until you do, a worker that still finds the TV token with a non-loopback CLAUDE_MEM_WORKER_HOST and no local API token binds to 127.0.0.1 ( ::1 for an IPv6 host) and logs a SECURITY error, so the full API is never open to the network without a token. 
 Framing protection now covers every page the worker serves. 
 
 Already shipped in 15.20.0 and 15.21.0 
 The rest of the same review reached you in 15.20.0: 
 
 Setup: a step bar, Back on every screen, plain errors, and Stop import ( #6233 ). 
 Classic viewer: one header row, a searchable project picker, "Find in this session", and no React error 185 at the end of a long timeline ( #6229 ). 
 Import from Mem0 and Supermemory: acceptance fixes ( #6206 ). 
 Fixes: Codex Desktop sessions are read live on macOS ( #6285 , thanks @MaxWang007 ), and the worker starts when settings.json is not valid JSON ( #6259 ). 
 
 15.21.0 followed: Code Mode starts with claude-mem enabled ( #6278 ), auto-clear resumes with a continuation prompt ( #6294 ), Hermes Desktop and GitHub Copilot in VS Code connect over MCP ( #6284 , #6286 ), and setup finishes when your prompt history is too large for one upload ( #6280 ). 
 Full notes: 15.20.0 and 15.21.0 . 
 Also new 
 
 The SessionStart banner is a card in Claude Code terminals ( #6274 ). On Claude Code 2.1.326 or later, the Rules + Tools line, "Previously" and the timeline are drawn as one framed card. A session mirrored to the Claude app shows one line instead of the hook's name in front of every line of the banner. 
 
 Fixes 
 
 The worker keeps answering while it works through a backlog. Health checks, hooks and the viewer no longer wait behind:
 
 a hook spool backlog: the drain reads files in parallel batches of 64 ( #6260 , thanks @Zhong-fan ) and removes and claims them without blocking ( #6296 , from #6254 by @Afloat16 ); reported in #6247 by @soarkit ; 
 the project list at worker start, which read every row and now reads the project indexes ( #6270 ; reported in #6246 by @soarkit ); 
 the Claude CLI check that corpus prime and query run on a cache miss ( #6256 , thanks @Afloat16 ; reported in #6250 by @soarkit ); 
 Chroma sync's checkpoint, which was rewritten for every row (about 28 MB of writes for 2,000 rows) and is now written once per 250 ms ( #6204 , thanks @Zhong-fan ; reported in #6203 by @soarkit ). 
 
 
 Folder CLAUDE.md files: updates fetch up to 8 folders at a time instead of one by one ( #6264 ; reported in #6248 by @soarkit ), claude-mem generate reads a project's observations once instead of once per folder ( #6265 ; reported in #6249 by @soarkit ), and a failed folder update is logged with its folder and tried again by the next observation for that folder ( #6208 , thanks @0xABCD01 ). 
 Long Bash output keeps its end ( #6292 ; reported in #6282 by @micronox ). When Claude Code cut an output over about 30,000 characters and saved the full text to a file, the memory came from the start only, so the last lines (test summaries, final errors) were lost. claude-mem now reads the end from that file. 
 Native memory notes: a note with type: at the top of its frontmatter keeps its category ( #6244 ), and a note's project is found when the transcript's first prompt is long ( #6272 ), thanks @Afloat16 . 
 Recent sessions include adopted worktrees ( #6268 , thanks @Afloat16 ). After a worktree was merged into its parent, OpenClaw's claude-mem-recent showed no previous sessions. 
 Search: Chinese and Japanese terms inside longer unspaced words are found in corpus evidence ( #6213 , thanks @liuyinchu ). smart_outline , smart_search and smart_unfold find JavaScript functions defined by assignment, such as exports.read = function ... ( #6245 ), and each Java method overload unfolds on its own ( #6257 ), thanks @Afloat16 . 
 Quieter error reports: a context read that passes the 120-second reader deadline names the slow read and logs a warning, not an error ( #6255 ), and on Windows a spool entry that Windows keeps locked gets one warning instead of an error report on every drain ( #6269 ). 
 Two failures that were dropped are logged now ( #6302 ): auto-clear says so in the transcript when it could not hand Claude its request to save the work state, and the server logs why /v1/info could not read the vector search status. 
 Turkish: clearer My Work wording and an up-to-date Turkish README ( #6287 , thanks @alkank ). 
 
 For contributors 
 
 The commit-message test that needs bash 4 is skipped on macOS's bash 3.2, and still runs on Linux CI ( #6297 ).

</details>