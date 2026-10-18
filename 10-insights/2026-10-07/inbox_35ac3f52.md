---
id: inbox_35ac3f52
date: 2026-10-07
source_ref: "[[00-inbox/2026-10-07/0256-claude-code-releases-v2-1-293-09e8]]"
title: "v2.1.293"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.293
source: claude-code-releases
published_at: 2026-10-07T18:10:20+00:00
fetched_at: 2026-10-18T02:59:37.250291+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.293 新增 Claude Haiku 5.5（claude-haiku-5-5），成為 Anthropic API 上預設的 Haiku 模型，具備 1M context，價格為每百萬 token $0.10 輸入／$0.50 輸出（prompt 超過 100K 時為 $0.50／$2.50）。同版新增 subagentStatusLine payload 的 agentType 欄位，讓腳本可區分自訂 subagent 類型；並為 mods 的 $.tool.register 新增 isDeferred，設為 false 時會從一開始就把工具 schema 列在 prompt，而不是藏在 tool search 後面。修正項目繁多，包括 context compaction 前最後動作被誤判為已完成而導致撤回或重做、HTTP MCP 連線的記憶體洩漏、/ultrareview 上傳在 Linux 的誤拒、Remote Control 與雲端 session 的串流與重複上傳問題，以及 path-scoped rules 與巢狀 CLAUDE.md 在 Bash 用 cat/head/tail/sed -n/grep 檢視單一檔案時未載入的問題。另有改進 Team/Enterprise 啟動速度（較早抓取 policy 與 managed settings，卡住的請求 3 秒後重試）、claude.ai skill 同步在無使用時改為約每 40 分鐘檢查、以及數項 Claude Tag（Slack）修正，並回復 2.1.281 與 2.1.290 的兩項先前變更。"
key_points:
  - "新增 Claude Haiku 5.5（claude-haiku-5-5）為預設 Haiku：1M context，$0.10/$0.50 per Mtok（超過 100K 的 prompt 為 $0.50/$2.50）"
  - "修正 compaction 前最後動作被當成已完成導致撤回/重做，以及 HTTP MCP 連線保留所有已送出請求的記憶體洩漏"
  - "修正 path-scoped rules 與巢狀 CLAUDE.md 在 Bash 以 cat/head/tail/sed -n/grep 檢視單檔時不載入的問題"
tags: [claude-code, claude-haiku-5-5, pricing, mcp, bugfix]
topics: [agents.coding_agents, foundation_models.claude, agents.mcp]
importance: 4
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.293

Claude Code v2.1.293 新增 Claude Haiku 5.5（claude-haiku-5-5），成為 Anthropic API 上預設的 Haiku 模型，具備 1M context，價格為每百萬 token $0.10 輸入／$0.50 輸出（prompt 超過 100K 時為 $0.50／$2.50）。同版新增 subagentStatusLine payload 的 agentType 欄位，讓腳本可區分自訂 subagent 類型；並為 mods 的 $.tool.register 新增 isDeferred，設為 false 時會從一開始就把工具 schema 列在 prompt，而不是藏在 tool search 後面。修正項目繁多，包括 context compaction 前最後動作被誤判為已完成而導致撤回或重做、HTTP MCP 連線的記憶體洩漏、/ultrareview 上傳在 Linux 的誤拒、Remote Control 與雲端 session 的串流與重複上傳問題，以及 path-scoped rules 與巢狀 CLAUDE.md 在 Bash 用 cat/head/tail/sed -n/grep 檢視單一檔案時未載入的問題。另有改進 Team/Enterprise 啟動速度（較早抓取 policy 與 managed settings，卡住的請求 3 秒後重試）、claude.ai skill 同步在無使用時改為約每 40 分鐘檢查、以及數項 Claude Tag（Slack）修正，並回復 2.1.281 與 2.1.290 的兩項先前變更。

### 重點
- 新增 Claude Haiku 5.5（claude-haiku-5-5）為預設 Haiku：1M context，$0.10/$0.50 per Mtok（超過 100K 的 prompt 為 $0.50/$2.50）
- 修正 compaction 前最後動作被當成已完成導致撤回/重做，以及 HTTP MCP 連線保留所有已送出請求的記憶體洩漏
- 修正 path-scoped rules 與巢狀 CLAUDE.md 在 Bash 以 cat/head/tail/sed -n/grep 檢視單檔時不載入的問題

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.293)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added Claude Haiku 5.5 ( claude-haiku-5-5 ), now the default Haiku model on the Anthropic API — 1M context, $0.10/$0.50 per Mtok ($0.50/$2.50 for prompts over 100K) 
 Added agentType to the subagentStatusLine payload, so scripts can tell custom subagent types apart 
 Added isDeferred to $.tool.register for mods: false lists the tool's schema in the prompt from the start instead of behind tool search 
 Fixed Claude sometimes treating its own last actions before a context compaction as done after it, and retracting or redoing finished work 
 Fixed a memory leak where an HTTP MCP connection kept every request it had sent until it closed 
 Fixed a message sent while Claude was working being lost when ← moved the session to the background; if a queued message can't move, ← now stays put and says so 
 Fixed /model effort ←/→ wrapping past the highest or lowest level, which could accidentally save Low as a model's default effort 
 Fixed /tui disconnecting Claude in Chrome in a session started with --chrome , and ignoring --no-chrome 
 Fixed Claude being told to continue or message subagents with SendMessage in sessions, including resumed ones, where a host, a permission rule or a --tools list removed that tool 
 Fixed subagents and --agent sessions being told a built-in tool was disabled for the whole session when only their own tool list left it out 
 Fixed a claude.ai-synced skill's edited description sometimes not reaching the model until a new conversation or /clear 
 Fixed claude logs , stop , kill , rm and claude daemon status , stop , uninstall sometimes signing you out when your login had expired or was about to 
 Fixed the footer's agents count disappearing after a momentary failure to read the sessions folder (for example, too many open files) 
 Fixed a custom agent named worker being shown as "Agent" when it starts, and the agent detail dialog's title losing the agent type once the agent finishes 
 Fixed the Artifact tool's transcript row briefly reading Artifact("(unprintable path)") while a publish call was still streaming in 
 Fixed the /ultrareview upload on Linux wrongly refusing some repositories, such as one inside another checkout, over a settings file that "could not be parsed" while a sandboxed command was running 
 Fixed the /ultrareview upload's refusal over split-index files advising a git command that could leave git unable to read its index 
 Fixed replies in very long Remote Control and cloud sessions that could still appear a block at a time instead of streaming in 
 Fixed Remote Control uploading a session's starting history again after every credential recovery 
 Fixed PushNotification reporting "Remote Control inactive" in sessions started with claude remote-control 
 Fixed a mod's hooks on classic.* events being skipped while the plugin hooks worker restarts, which left settings hooks to answer without them 
 Fixed claude plugin test failing for mods that call $.session.append ; tests can read the appended rows back with the new mock.session 
 Fixed claude plugin eval refusing every Bash-granting run on Macs with Docker Desktop (links under ~/.docker/bin ); the refusal now names which part of a credential store held the link 
 Fixed the Claude apps gateway refusing to start when a desktop policy sets Claude Desktop's built-in browser keys, such as builtinBrowserEnabled 
 Fixed claude agents offering bypass permissions that background sessions then ignored when consent was saved only in .claude/settings.local.json or a --settings file; it now asks for consent first, and a session that ignores bypass shows a short notice that stays 
 Fixed ← backgrounding a session after 10 seconds while the prompt held unsent text (it now cancels the move) or a question was waiting for your answer 
 Fixed Esc, or No without feedback, on a permission prompt not stopping the turn when ← had just been pressed to move the session to the background 
 Fixed the agents view briefly replacing the session list with placeholder rows when the sessions folder could not be read (for example, too many open files) 
 Fixed path-scoped rules and nested CLAUDE.md files not loading when Claude views a file with a single-file cat, head, tail, sed -n or grep command in the Bash tool instead of the Read tool 
 Fixed pasted text that begins and ends with the same words sometimes being sent to Claude as if it had been typed 
 Fixed a skill name in pasted text being treated as typed when an accent typed or pasted right after the paste merged into its last letter 
 Fixed /feedback returning to the drafts list after Ctrl+O or Ctrl+Z while a report was sending, leaving the send impossible to cancel 
 Fixed claude purge stopping silently (exit 0, or a hang in a terminal) when a file or folder could not be deleted; it now deletes the rest, lists what it could not delete, and exits 1 
 Fixed keybindings.json checks: a lone " " (space key) is no longer reported as an error, and keys like "ctrl+ k" now get a warning 
 Fixed vim mode &gt;&gt; and &lt;&lt; on a line of only spaces leaving the cursor past the end of the line, where a following x deleted nothing 
 Fixed vim mode: after deleting whole lines in Visual mode ( V then d ) the cursor lands on the first non-blank, and . after it acts on the cursor's line 
 Windows: Fixed stopping a status line, hook, or shell command sometimes terminating an unrelated process that had been given the same process ID 
 Reverted the auto mode denial message change from 2.1.281 that told Claude a denial covers the outcome, not only the exact command 
 Reverted the 2.1.290 fix for cloud sessions staying asleep after a container restart lost a pending /loop wakeup or scheduled task; Claude is no longer told, and the session stays asleep 
 Improved startup for Team and Enterprise organizations: policy and managed settings are fetched earlier, and a stalled request is retried after 3 seconds 
 Improved Claude in Chrome: fewer page actions are refused when the browser is slow to report its tabs 
 Improved the Claude in Chrome message in cloud sessions when the browser can't be reached: if you belong to more than one organization, it now says the extension must be signed in to the same one, and how to change that 
 Improved the Bash edit diff note to say the listed files changed while the command ran, which can include writes by other processes 
 Improved artifacts: Claude pins libraries to exact versions two weeks old or older 
 Changed claude.ai skill syncing to check for changes about every 40 minutes, instead of every 10, while no session is in use 
 Changed the order of agent lists and of MCP servers announced to the model: names with non-ASCII characters now sort after ASCII names 
 Changed OpenTelemetry claude_code.at_mention logging to emit at most 100 agent and 100 MCP-resource events each time a prompt is read 
 Self-hosted runner: Changed the orchestrator to sleep 4 to 6 seconds between polls instead of a constant 5, so several replicas for one environment stop polling at the same moment 
 [Claude Tag] Fixed Claude in Slack saying a workspace isn't set up in Enterprise Grid channels shared across workspaces when Slack labels a message with a workspace that isn't connected 
 [Claude Tag] Fixed Claude in Slack stopping mid-task in a channel when an admin changed the channel's connectors, plugins, skills or rules; the change now applies once Claude finishes 
 [Claude Tag] Fixed asking Claude in Slack to run a thread's routine now with extra notes starting a separate run that couldn't post back; the run now continues in that thread 
 [Claude Tag] Fixed an access bundle's Add a connector dialog in Claude Tag admin settings showing every Google connector as connected after one Google sign-in 
 [Claude Tag] Improved Claude Tag admin settings to list an Enterprise Grid that isn't connected yet, with a Connect button 
 [Claude Tag] Changed Claude in Slack to join announcement channels, where only admins can post, without posting its intro 
 [Claude Tag] Changed the limit on channel rules in Claude Tag admin settings from 20 to 50 for each workspace and for the organization-wide Slack page 
 [Code Review] Improved Code Review's Add a repository dialog to list each repository that couldn't be added and why, such as missing GitHub write access

</details>