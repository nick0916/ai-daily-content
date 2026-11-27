---
id: inbox_af94f5d2
date: 2026-11-25
source_ref: "[[00-inbox/2026-11-25/0051-claude-code-releases-v2-1-332-3c7e]]"
title: "v2.1.332"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.332
source: claude-code-releases
published_at: 2026-11-25T01:32:14+00:00
fetched_at: 2026-11-27T00:57:54.516046+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版主要在修大量當機、卡死與模型回退問題，同時新增 MCP 技能與一個 hook 事件。 **Why** 長時間使用下，hook 輸出無限、MCP 伺服器狂吐 stdout、超長輸入等情況會讓終端卡死或記憶體暴增，在第三方雲端（Bedrock、Foundry 等）上模型被拒時也會直接失敗。 **How** 對超長 hook 日誌截斷（超過約 50,000 字元）、對卡住的具名管道讀取設 20 秒逾時、壓縮失敗時改請模型寫更短的摘要，模型被拒時則往同系列較舊版本逐級回退。 **What** Claude Code v2.1.332 新增 MCP 伺服器提供的技能（beta，在 / 選單顯示為 server:skill）、PreSkillShellCommand hook 事件（可拒絕技能或指令載入時的內嵌 shell 指令）、OpenTelemetry 的 assistant_response 事件，並在啟動標頭顯示 Cyber Verification Program 存取等級。另修正 Bedrock Mantle 上 sonnet 別名誤解析為 Haiku 4.5 的問題，現在指向 Sonnet 5（非 Sonnet 5.5）；本篇內容在來源處被截斷，以上僅涵蓋可見部分。"
key_points:
  - "新增 MCP 伺服器技能（beta，/ 選單顯示 server:skill）與 PreSkillShellCommand hook 事件，可在載入時拒絕技能的內嵌 shell 指令；2.1.331 及更舊版本若設定檔提到該事件，啟動時會跳出對話框"
  - "多項卡死修正：hook 輸出無限、本地 MCP 伺服器洪水式輸出 stdout（且 Ctrl+C 失效）、超過約 50,000 字元的 hook 日誌改為截斷、具名管道讀取 20 秒後失敗"
  - "第三方雲端模型回退修正：Bedrock／Google Cloud Agent Platform／Foundry 上模型被拒時，會逐級退到同系列較舊且可用的模型；Bedrock Mantle 的 sonnet 別名改為 Sonnet 5（非 5.5），沒有 Sonnet 5 權限的帳號會報錯"
tags: [claude-code, release-notes, mcp-skills, hooks, bug-fixes]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.332

Claude Code 這版主要在修大量當機、卡死與模型回退問題，同時新增 MCP 技能與一個 hook 事件。

**Why** 長時間使用下，hook 輸出無限、MCP 伺服器狂吐 stdout、超長輸入等情況會讓終端卡死或記憶體暴增，在第三方雲端（Bedrock、Foundry 等）上模型被拒時也會直接失敗。

**How** 對超長 hook 日誌截斷（超過約 50,000 字元）、對卡住的具名管道讀取設 20 秒逾時、壓縮失敗時改請模型寫更短的摘要，模型被拒時則往同系列較舊版本逐級回退。

**What** Claude Code v2.1.332 新增 MCP 伺服器提供的技能（beta，在 / 選單顯示為 server:skill）、PreSkillShellCommand hook 事件（可拒絕技能或指令載入時的內嵌 shell 指令）、OpenTelemetry 的 assistant_response 事件，並在啟動標頭顯示 Cyber Verification Program 存取等級。另修正 Bedrock Mantle 上 sonnet 別名誤解析為 Haiku 4.5 的問題，現在指向 Sonnet 5（非 Sonnet 5.5）；本篇內容在來源處被截斷，以上僅涵蓋可見部分。

### 重點
- 新增 MCP 伺服器技能（beta，/ 選單顯示 server:skill）與 PreSkillShellCommand hook 事件，可在載入時拒絕技能的內嵌 shell 指令；2.1.331 及更舊版本若設定檔提到該事件，啟動時會跳出對話框
- 多項卡死修正：hook 輸出無限、本地 MCP 伺服器洪水式輸出 stdout（且 Ctrl+C 失效）、超過約 50,000 字元的 hook 日誌改為截斷、具名管道讀取 20 秒後失敗
- 第三方雲端模型回退修正：Bedrock／Google Cloud Agent Platform／Foundry 上模型被拒時，會逐級退到同系列較舊且可用的模型；Bedrock Mantle 的 sonnet 別名改為 Sonnet 5（非 5.5），沒有 Sonnet 5 權限的帳號會報錯

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.332)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added skills from MCP servers (beta). They show as server:skill in the / menu; other skills keep their names 
 Added a PreSkillShellCommand hook event that can refuse a skill or command's inline shell commands as it loads; on 2.1.331 and older, a settings file naming it opens a dialog at start 
 Added "Always deliver" to the prompt for held messages from other sessions 
 Added a footer line that stays while a flagged message has your session on a different model, until you pick one with /model 
 Added an OpenTelemetry assistant_response event for text Claude sends through SendUserMessage or Cowork's message tool, when response logging is on 
 Added a warning in VS Code and Desktop's Code tab when part of a session couldn't be saved, saying how to save it with /compact 
 Added a notice in VS Code and Desktop's Code tab when a resumed session's earlier messages weren't loaded, as the terminal already shows 
 Added your Cyber Verification Program access tier to the startup header, beside the model name when your tier applies to that model and you're signed in with a claude.ai account 
 Fixed claude auth login reporting Login successful. when a claude.ai login could not be saved: it now exits 1 and says what to check, such as a leftover lock file or a full disk 
 Fixed Read, @-mentions and compaction hanging on a named pipe that nothing writes to, such as a .env mounted by a locked secrets manager; the read now fails after 20 seconds 
 Fixed turns ending in "Prompt is too long" after repeated auto-compaction failures when one more compaction at the context limit could have kept them going 
 Fixed compaction failing when a summary kept running past the output limit: after three cut-off replies, the last try now asks for a shorter summary 
 Fixed a freeze when a permission rule or hook condition with several wildcards was checked against a long command 
 Fixed freezes and runaway memory use in most cases while a hook prints output without end 
 Fixed a freeze and context overflow when a hook blocks or fails during a turn, or after /compact , with a very large log; text over about 50,000 characters is now shortened 
 Fixed the terminal freezing, and ignoring Ctrl+C, while a local MCP server floods its standard output 
 Fixed a freeze when a prompt or piped input holds an @ followed by a very long unbroken string, such as minified CSS with an embedded font 
 Fixed a long freeze when opening a rewind point after a large tracked file was rewritten 
 Fixed SSE MCP servers hanging or refusing every tool call after their event stream was cut and came back on a new endpoint or not at all, until reconnected by hand 
 Fixed Remote Control showing a session in the desktop app, VS Code or the Agent SDK as running while it waited there on a dialog or an MCP server's question 
 Fixed a usage limit being reported as reached to Remote Control, IDE and SDK clients after it had already reset 
 Fixed CLAUDE.md and rules files being sent to the model a second time, in most cases, after a session moves into a worktree under .claude/worktrees with EnterWorktree or is resumed there 
 Fixed tool calls that never ran being counted as done in a claude.ai chat's summary line after you declined a permission prompt in a session that had restarted 
 Linux: Fixed the Bash edit diff showing an unchanged symlink as edited after Claude had read the file through it 
 Fixed resuming a session and /stats freezing for seconds when a transcript holds many damaged lines 
 Fixed a family name such as sonnet in --fallback-model being dropped when availableModels allows only an older version of it 
 Fixed keys lagging for seconds while /stats reads large session transcripts, also after the dialog is closed, and with debug logging on while a language server floods its stderr 
 Fixed a session failing when the cloud refused its default model and an availableModels list that isn't enforced named neither it nor an older model of that family 
 Fixed an enforced list of older models failing on Google Cloud's Agent Platform and Foundry when the first is refused: it now steps down to the next in that family, if listed newest first 
 Fixed opus failing on Bedrock, Google Cloud's Agent Platform and Foundry behind a gateway that refuses a model in its own words: it now steps down to an older model that answers 
 Fixed the start-up model upgrade offer on Bedrock and Google Cloud's Agent Platform naming a model that your availableModels list leaves out 
 Fixed Bedrock sub-agents failing when your account lists no profile for their model in the parent's region: they now use the model's own profile, which can be outside that region 
 Fixed Foundry sessions leaving a model family when an admin's list blocks the version sonnet , opus or haiku points to: they now use its newest allowed version under a built-in or mapped name 
 Fixed the sonnet alias on Bedrock Mantle resolving to Haiku 4.5: it now means Sonnet 5, not Sonnet 5.5, and an account without Sonnet 5 gets an error, so enable it first 
 Fixed Ctrl+C at the prompt starting a new turn, and a double Ctrl+C not exiting, when a background agent it stopped had an unread subagent report 
 Fixed /install-github-app ticking a workflow again after going back with Esc 
 Fixed dictated text past 10,000 characters being lost 
 Fixed raw "JSON Parse error" and "The operation was aborted." API errors when the non-streaming retry got a broken response or was interrupted 
 Fixed Esc not stopping computer use between actions on macOS when Claude Code's window or an app you allowed is in front; an Esc meant for that app's popup now stops computer use instead 
 Fixed a rare hang when a helper command, such as an API key helper, ran past its time limit 
 Fixed selecting text in fullscreen pushing the footer's right-hand label onto a second row, which moved the text under the mouse and could copy the wrong line 
 Fixed a PreToolUse hook's reason for asking not showing on terminal Read, Grep, Glob, Edit and Write prompts ( #102892 , #105343 ) 
 Fixed temp_* folders piling up in ~/.claude/plugins/cache when a downloaded plugin couldn't be copied into place 
 Fixed --effort being ignored when starting an interactive session with --environment while CLAUDE_CODE_EFFORT_LEVEL is set to the same level 
 Fixed headless and cloud sessions reporting a foreground fork's Agent call as finished the moment the fork started 
 Fixed local MCP servers seeing a new session ID after a Remote Control session's process restarts 
 Fixed idle compaction being skipped for subscribers still well under their weekly limit 
 Fixed an @-mentioned text file with an extension being silently dropped when even its first 2,000 lines exceed the read limit; Claude is now told its size and how to read it 
 Fixed the plugin "not cached" error pointing to /plugin instead of /reload-plugins , the command that reloads plugins 
 Fixed self-hosted runner sessions failing their first clone under Anthropic-managed git when the machine's git config has an includeIf "gitdir:" or (git 2.44 to 2.46) "onbranch:" section 
 Fixed replies that start with phrases like "You've used" or "You've hit your" showing as a red usage limit error 
 Fixed a resumed conversation sometimes missing its last messages after a crash or kill on Bedrock, Google Cloud's Agent Platform, Foundry and other third-party providers 
 Fixed NotebookEdit saving an invalid notebook when an edit changes a cell's type; turning a cell with attachments into code is now refused 
 Fixed a long README in a design system moved from standalone Claude Design losing its list of files to load when Claude starts a deck or design 
 Fixed MCP tool calls failing with "malformed task handle" when the server's task ID is longer than 128 characters; IDs of up to 1,024 characters now work 
 Self-hosted runner: Fixed --configure-git sometimes reporting a hung git --version as a git that isn't on PATH 
 Fixed task ids being reused and deleted tasks coming back when several tasks were deleted or updated at once, and TaskGet listing completed tasks as blockers 
 Fixed stale and repeated rows in the fullscreen Ctrl+R history picker when prompts share a timestamp 
 Fixed Code Mode silently skipping a tool call whose input has a list of over 4,096 items, and freezing on a very large typed array in a tool's input, which is now refused 
 Fixed Code Mode leaving a message unanswered when it was typed during a command and Esc was pressed before Claude replied; the message now starts a new turn, which a second Esc stops 
 Fixed Code Mode not telling Claude when a slow command moved to the background and left its script with empty output, or of the time limit on background commands in claude -p and the Agent SDK 
 Fixed Code Mode sometimes waiting for minutes on a command that had already been stopped 
 Fixed a typed slash command's inline shell commands not running in Code Mode after a background script's output arrived 
 Fixed Code Mode sessions in the Agent SDK and claude -p sometimes losing Claude's last reply on resume after being stopped while a script was running 
 Remote Control: Fixed sessions hosted by the desktop app or VS Code showing as idle while /compact runs 
 Fixed a session sometimes losing its "needs input" status after a background task's report in Claude Desktop 
 Fixed Grep: -o missing an empty match at the end of a file with no last newline, -o with multiline adding an empty line or misnumbering lines in non-UTF-8 files, and -A and -B ignored beside a zero -C 
 Fixed unbinding a chord in keybindings.json still leaving its first key waiting for a second when it was spelled meta and bound as alt , or the reverse 
 Fixed moving an empty session to the background sometimes failing with "Couldn't load transcript from file" 
 Fixed OpenTelemetry reporting a failed mcp_server_connection event at each start for a built-in server that isn't turned on for the account 
 Fixed Esc not stopping a Bash command while it waited for its file diff in large or slow git repositories, which held the next message 
 Fixed pasted links and relative paths ending in an image file name appearing late and swallowing an Enter pressed right after 
 Fixed /mcp reconnect all and /mcp disable all counting a built-in server that isn't turned on for the account 
 Fixed interrupting a turn while a mod's turn.step hook was waiting showing "user-cancel" as an error instead of "Interrupted" 
 Fixed ~/.claude.json being reported as corrupted when another session was in the middle of saving it 
 Fixed web searches failing with an API error when Claude's list of allowed or blocked domains was empty or had duplicates 
 Fixed resuming a paused workflow in Code Mode waiting for minutes while other background work was running 
 Fixed subagents in Code Mode failing with "Agent stalled" and losing their command when a script ran for more than 10 minutes 
 Improved claude plugin marketplace add on Windows to wait and try again in some cases when another program, such as a virus scanner, briefly holds the downloaded files 
 Windows: Improved stability on some company PCs, where Claude Code could exit with no output shortly after start 
 Improved computer use setup: the Screen Recording permission prompt can now restart Claude Code and resume the chat 
 Improved computer use to take less context until Claude uses it 
 Improved the error when a proxy or gateway cuts or damages a compressed response: a turn now ends in plain words instead of raw "ZlibError fetching" text 
 Improved /context : shorter output in fullscreen, so the total is less likely to scroll off in a short window, and the legend names its unit once 
 Improved peak memory use and speed of /usage on machines with many recent sessions 
 Improved /permissions to refuse a rule that would be skipped at the next start, such as rm -rf with no tool name, and to show the reason 
 Improved resuming a session in Code Mode: Claude is now told up front that its earlier 

[... truncated for safety ...]

</details>