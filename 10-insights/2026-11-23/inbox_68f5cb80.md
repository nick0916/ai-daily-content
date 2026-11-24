---
id: inbox_68f5cb80
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-claude-code-releases-v2-1-331-2787]]"
title: "v2.1.331"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.331
source: claude-code-releases
published_at: 2026-11-23T21:34:41+00:00
fetched_at: 2026-11-24T02:14:18.677872+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版主要補齊雲端平台支援、可觀測性，並修掉大量終端機與 VSCode 的小問題。 **Why** 企業用戶在不同雲端、代理與 Windows 受管設定下，常遇到連線、權限與顯示異常。 **How** 擴充 Code Mode 到多個雲端平台、在 trace span 加入 gen_ai.* 欄位、新增 claude doctor 的 API 連線檢查，並逐項修正 MCP、compact、plugin 與 VSCode 行為。 **What** Claude Code v2.1.331：Code Mode 支援 Amazon Bedrock、Google Cloud Agent Platform、Microsoft Foundry 與 Claude Platform on AWS；新增 CLAUDE_CODE_DISABLE_RESPONSE_COMPRESSION 與 plugin optionalDependencies；修正 MCP 工具呼叫最久卡 30 分鐘的問題。另預告 2026-11-30 起，managed extraKnownMarketplaces 的 plugin marketplace 將預設自動更新（可設 \"autoUpdate\": false 退出）。"
key_points:
  - "Code Mode 在 Amazon Bedrock、Google Cloud Agent Platform、Microsoft Foundry、Claude Platform on AWS 的終端機 session 可用"
  - "claude_code.llm_request trace span 新增 gen_ai.usage.*、gen_ai.response.model、gen_ai.operation.name；input_tokens 含 prompt cache tokens"
  - "2026-11-30 起 managed extraKnownMarketplaces 預設自動更新，可用 \"autoUpdate\": false 關閉；Windows 用戶升級前應檢查 registry 的 managed settings（HKLM 優先於 managed-settings.json）"
tags: [claude-code, release-notes, code-mode, plugins, observability]
topics: [agents.coding_agents, agents.mcp]
importance: 3
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.331

Claude Code 這版主要補齊雲端平台支援、可觀測性，並修掉大量終端機與 VSCode 的小問題。

**Why** 企業用戶在不同雲端、代理與 Windows 受管設定下，常遇到連線、權限與顯示異常。

**How** 擴充 Code Mode 到多個雲端平台、在 trace span 加入 gen_ai.* 欄位、新增 claude doctor 的 API 連線檢查，並逐項修正 MCP、compact、plugin 與 VSCode 行為。

**What** Claude Code v2.1.331：Code Mode 支援 Amazon Bedrock、Google Cloud Agent Platform、Microsoft Foundry 與 Claude Platform on AWS；新增 CLAUDE_CODE_DISABLE_RESPONSE_COMPRESSION 與 plugin optionalDependencies；修正 MCP 工具呼叫最久卡 30 分鐘的問題。另預告 2026-11-30 起，managed extraKnownMarketplaces 的 plugin marketplace 將預設自動更新（可設 "autoUpdate": false 退出）。

### 重點
- Code Mode 在 Amazon Bedrock、Google Cloud Agent Platform、Microsoft Foundry、Claude Platform on AWS 的終端機 session 可用
- claude_code.llm_request trace span 新增 gen_ai.usage.*、gen_ai.response.model、gen_ai.operation.name；input_tokens 含 prompt cache tokens
- 2026-11-30 起 managed extraKnownMarketplaces 預設自動更新，可用 "autoUpdate": false 關閉；Windows 用戶升級前應檢查 registry 的 managed settings（HKLM 優先於 managed-settings.json）

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.331)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added Code Mode support in terminal sessions on Amazon Bedrock, Google Cloud's Agent Platform, Microsoft Foundry and Claude Platform on AWS 
 Added oidc.groups_jsonpath to the Claude apps gateway, to read groups from the matching entries of a list of objects with a small subset of JSONPath (RFC 9535) 
 Added an API connectivity section to claude doctor that reports whether the API can be reached, with the HTTP status or the error, or says why it wasn't tested 
 Added a notice when tap-mode voice dictation stops by itself, after 15 seconds without recognized speech or at its 2-minute limit 
 Added CLAUDE_CODE_DISABLE_RESPONSE_COMPRESSION to ask for uncompressed model responses behind a proxy that cuts compressed ones off; not advised yet for self-hosted runners or Remote Control 
 Added CLAUDE_GATEWAY_IDP_CONNECT_BY_HOSTNAME=1 for Claude apps gateways: with oidc.use_proxy: true , sign-in requests hand the proxy an https IdP's hostname even with NO_PROXY set 
 Added gen_ai.usage.* , gen_ai.response.model and gen_ai.operation.name to claude_code.llm_request trace spans; gen_ai.usage.input_tokens includes prompt cache tokens 
 Added optionalDependencies to plugin manifests: plugins that install with the plugin listing them and can be disabled or uninstalled on their own 
 Fixed MCP tool calls hanging for up to 30 minutes on some malformed replies from a local or WebSocket server 
 Fixed PushNotification telling a headless run, such as a scheduled one, that the terminal was active in its first minute, instead of saying whether a mobile push was requested 
 Fixed /install-github-app skipping the repository step after setup warnings when no repository was found, and Esc not going back from its workflow list and sign-in steps 
 Fixed one-line tool results cut with no ellipsis in narrow windows, Markdown stars in the Auto mode tab of /permissions, and a hook's reason to stop a forked skill showing twice 
 Fixed /diff hiding its key hints and not selecting files in windows of 24 to 26 rows, and leaving out files added with git add -N in a repository with no commits 
 Fixed the first-run theme list showing too few themes in short windows, and /usage and other tall screens coming out garbled there 
 Fixed /bug in fullscreen hiding its Yes and No answers behind a long report, and Yes staying out of view in very short windows 
 Fixed /compact and auto-compact sometimes losing part of the conversation summary when the summary quoted certain XML tags 
 Fixed Claude not being told when permission rules on the Agent tool dropped its queued message to a subagent that had already ended 
 Fixed a Remote Control message sometimes showing above the reply that was finishing when it was sent 
 Fixed Stop hooks that read the transcript missing the last reply in Claude Desktop; SubagentStop hooks now wait for it too 
 Fixed turns and subagents failing in cloud sessions, or timing out on long replies elsewhere, when a reply went silent while Claude was still thinking; Claude Code now tries the request once more 
 Fixed Esc and Stop waiting about a minute or more when the contents of a cloud or network file that Claude is reading stall 
 Fixed Code Mode sessions resumed with --resume or --continue in another permission mode losing thinking and the prompt cache; one begun in a mode that asks keeps that mode's limits on scripts 
 Fixed Code Mode sending a request about every second when a ! or slash command was typed while a script was running 
 Fixed an interrupted or failed plugin update leaving a partial plugin folder that later loaded with skills or other components missing ( #102186 ) 
 Windows: Fixed file writes on FAT32 and exFAT drives asking for permission every time in some plugin sessions 
 Fixed Claude failing to read a notebook that has a null output or an error output with no traceback 
 Fixed a rewind deleting files after a restore had failed 
 Fixed auto mode sometimes refusing Claude's call to stop a /loop, which left the next wake-up to fire 
 Fixed a Workflow agent's background shells and MCP servers sometimes being left running after it handed back its report 
 Windows: Fixed /desktop downloading the older Claude Desktop installer, and asking for an update when an older install's folder was left behind 
 Fixed claude plugin install , marketplace add and similar commands hanging with no output when managed settings needed an approval that could not be asked for 
 Fixed a permission rule on a subagent's model, such as Agent(model:*) , blocking Claude's follow-up message to a subagent started on this version with no model named 
 Fixed PermissionRequest hooks not saving Skill(name:*) allow rules outside local settings 
 Fixed "Ask your admin" asking to raise your own limit when your team's pooled group budget blocked you, and saying "Request sent" when an admin had approved your request in the last few minutes 
 Fixed Code Mode losing the middle of a long script output; Claude now gets a path to the uncut text ( #111373 ) 
 Fixed hold-to-talk dictation stopping early and losing words when Claude Code was busy 
 Fixed Code Mode with --bare not telling Claude what its scripts can call 
 Fixed a crash when a custom API endpoint returned a tool call with no tool name; the call now fails with an error and the session continues 
 Windows: Fixed a possible crash when the machine is almost out of memory 
 Fixed the CLI freezing on some replies, and quoted text sometimes going missing or showing twice 
 Windows: Fixed Claude Code refusing to start when managed settings in the registry contain non-ASCII characters such as Japanese ( #93280 ) 
 Windows: Fixed Remote Control clients showing no steps for a new subagent 
 Fixed @-mentions written as @file#10-12 attaching the whole file instead of those lines 
 Fixed Claude misreading a pasted artifact invitation link; it now asks you to accept the invitation and paste the artifact's own link 
 Fixed sandboxed Bash commands sometimes failing to start on a full temp disk, for sandboxes whose file rules keep commands out of the temp directory 
 Improved typing speed in screen reader mode, most of all in long sessions 
 Improved start-up time: a session started soon after another no longer waits for the model list, and one outside a git repository without .claude/settings.local.json no longer waits on git 
 Windows: Improved the speed of the first Bash command in a session on machines with no custom shell start-up files 
 Improved the plugin auto-update notice to name plugins it newly installs as dependencies, separately from updated plugins 
 Improved Code Mode tool search to show more of an MCP tool's description, with its limits, formats and defaults 
 Improved the Console sign-in link shown by /login and claude auth login --console : it is now much shorter 
 Improved Claude's list of your artifacts: it now marks web pages, so Claude is less likely to try opening one with the Claude Docs connector 
 Improved the folder trust prompts in short terminals: fullscreen /cd and /add-dir show their choices in fewer rows, and the prompt at launch keeps the folder path in view when it has many warnings 
 Changed the questions for stopping auto-connect in /ide and for /clear , /compact or /rewind in a subagent's view to list Yes first; they still start on No, so Down then Enter now answers No 
 Changed what a PermissionDenied hook's retry: true tells Claude: make the refused call again only if you asked for that call 
 Changed in a future release, on or after November 30, 2026: plugin marketplaces in managed extraKnownMarketplaces will auto-update by default. To opt one out, set "autoUpdate": false on its entry 
 Windows: Changed start-up with managed settings in the registry: check them before upgrading, as an HKLM policy outranks managed-settings.json and a broken value can stop the start 
 [VSCode] Added a warning and a link to the revoke page when you log out and the request to revoke your claude.ai login isn't confirmed 
 [VSCode] Added a notice before sending a very large selection or attached text file, and advice under "Prompt is too long" that names the large part and what to do next 
 [VSCode] Added "Add Cell to Chat" to the notebook cell menu, which attaches a cell with its outputs or error 
 [VSCode] Added "Fix with Claude Code" as a quick fix for errors and warnings and to failed tests in the test peek and the Test Results view, which puts the problem into the chat box 
 [VSCode] Added "Add to Chat" to the right-click menu of changed files in the Source Control view 
 [VSCode] Added "Resolve Merge Conflicts" to the editor title of a file with merge conflicts and to the Merge Changes group in Source Control 
 [VSCode] Fixed raw tags for selected code under a reworded prompt, the mode button flashing Manual, the slash menu hiding its highlighted row, a broken sign-in image, and a blinking Accept/Reject bar 
 [VSCode] Fixed a forked conversation overwriting the original conversation's plan file; a fork or rewind that can't copy the plan now shows a warning 
 [VSCode] Fixed voice dictation saying no speech was recognized when its connection closed or never opened; it now says the connection was lost or couldn't connect 
 [VSCode] Fixed an unsent side question being lost when its panel closes 
 [VSCode] Fixed Escape stopping Claude after renaming a session, and typing going nowhere after closing the session history with Escape 
 [VSCode] Fixed Rename, Mark as Unread and Add to Group saying "still connecting" on a tab that resumed a session from its history 
 [VSCode] Fixed wide tables and long paths cut off, long errors hiding their close button, errors out of view in the Add MCP server form and Chrome dialog, and plugin pictures ignoring the editor theme 
 [VSCode] Fixed later prompts and the message box covering the Rewind code dialog, and focus jumping from "Never mind" to "Rewind" when it finishes checking files 
 [VSCode] Fixed the command menu keeping an earlier match highlighted while you type more in its filter, so Enter could run the wrong row 
 [VSCode] Fixed the @ menu showing "No files found" before its first search results arrived, or when it couldn't search all files of a very large workspace, which it now says 
 [VSCode] Fixed Escape stopping Claude at a Remove or Delete confirmation in MCP, Hooks and Memory dialogs, on a side question panel's button or link, and on the Bookmarks button with its panel open 
 [VSCode] Fixed empty boxes showing instead of the + and − signs in diffs ( #73069 ) 
 [VSCode] Fixed the chat no longer following Claude's reply after the panel was resized, or hidden and shown again 
 [VSCode] Fixed a chat left in bypass permissions mode reopening in Auto mode instead of your initial permission mode when settings disable bypass 
 [VSCode] Fixed the chat panel freezing on some CSS code blocks and diffs 
 [VSCode] Fixed the context usage indicator disappearing after an API error, "Prompt is too long", or a slash command 
 [VSCode] Fixed a message queued behind a queued /clear being lost 
 [VSCode] Fixed Manage Plugins losing its search box or showing no message when a search has no match, and not saying that the list of available plugins failed to load 
 [VSCode] Fixed proposed changes to notebooks and files with a custom editor opening in a tab with no Accept or Reject that stayed open after the answer 
 [VSCode] Fixed the spend limit message telling Team and Enterprise members to run /usage-credits , which can't send a request to their admin from the panel 
 [VSCode] Fixed a written message being wiped by Tab on a command in the "/" button's menu or by a click on an onboarding suggestion 
 [VSCode] Fixed Claude continuing to edit files after you rewind code while it is working 
 [VSCode] Fixed typed text being lost after /tasks, /copy, /export, a skipped /feedback, or /plan while already in plan mode 
 [VSCode] Fixed the question card dropping a typed "Other" answer on Ctrl/Cmd+Enter, and sending

[... truncated for safety ...]

</details>