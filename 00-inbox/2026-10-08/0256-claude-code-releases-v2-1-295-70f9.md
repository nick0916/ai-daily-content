---
id: inbox_9ec5432c
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.295"
author: "ashwin-ant"
published_at: 2026-10-08T19:48:38+00:00
fetched_at: 2026-10-18T02:56:31.156563+00:00
content_hash: "70f90b04eb416b723645a4e90a86afa661b768ead777c0365be31690bb0f9fb8"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.295

What's changed 
 
 Added onFailure: "block" for command and HTTP hooks: a hook that can't start, times out, or exits with an unexpected code blocks the action instead of letting it through 
 Added Program Status Protocol (OSC 7501) support: terminals that implement it can show whether Claude Code is working, waiting on you, or done 
 Added quoted text to the /copy picker, so a drafted message copies without its &gt; markers 
 Added a warning to claude plugin install , enable , disable and marketplace add when the settings file they write to does not load 
 Added a line on stderr, when it is a terminal, that says what a claude -p run is waiting for when it stays open after its last turn 
 Added support for timeouts.upstream_ttfb_ms on the Claude apps gateway's Bedrock, Vertex, Foundry and other cloud upstreams: a value you set now limits how long a stream may take to start there, after which it fails over or gets a 502 
 Added a "Backgrounding cancelled" message when you stop the turn while ← is waiting for the current tool to finish 
 Added an optional models list to every Claude apps gateway upstream: only the listed models are sent there, on failover too, and one * in an entry is a wildcard 
 Added support for forceLoginMethod: "gateway" and forceLoginGatewayUrl in your own user settings on machines with no managed settings, so /login opens on that Claude apps gateway 
 Added advice to claude plugin validate when a plugin's README has no install line: it prints the line to paste and never changes the exit code, even with --strict 
 Added upstream_request_id to the Claude apps gateway's inference audit event: the request ID from Amazon Bedrock, the Anthropic API or another upstream, for support cases 
 Added $.ui.notify for mods: raises a native notification through your own notification setting and says which channel sent it 
 Added children to a mod's Button : strings and Text , so a row of a list is one pressable with a chip or a dim detail inside 
 Added CLAUDE_CODE_RETRY_WATCHDOG_MAX_WAIT_MS to limit how long unattended retry mode ( CLAUDE_CODE_RETRY_WATCHDOG ) waits out 429 and 529 errors 
 Added a request-id header to the Claude apps gateway's successful inference responses, so request_id in Claude Code telemetry matches the gateway's audit log 
 Fixed every request failing on a [1m] model when a gateway, Bedrock, Vertex or Foundry refuses the context-1m beta; Claude Code now resends without it 
 Fixed claude -p text output dropping earlier responses when background work started another turn; each turn's response now prints when the turn ends 
 Fixed remote MCP servers in headless and SDK sessions staying disconnected after an outage longer than 15 seconds, or reconnecting in a tight loop to a server that drops each connection right after it connects; repeated drops now back off, up to 30s 
 Fixed remote MCP connections being dropped when a server's error reply happened to contain a network error name 
 Fixed MCP servers that repeat a pagination cursor being asked for the same page up to 20 times at every connect 
 Fixed CSS, JavaScript and XML files returned by MCP tools being saved as .bin, which the Read tool refuses; font and icon files now get their own extension too 
 Fixed Bash tool calls failing when the model passes command_description instead of description 
 Fixed Claude in Chrome not applying a site deny rule written with port 80 ( host:80 ) to plain http:// pages on that host 
 Fixed /plugin 's Errors tab removing a marketplace that failed to load, and uninstalling its plugins, on Enter without asking first 
 Fixed claude plugin marketplace add reporting success for a marketplace whose name no plugin can be installed under; such an add is now refused 
 Fixed CLAUDE_AUTO_BACKGROUND_TASKS moving a subagent to the background while an edit or shell command waited behind it, which started that call before the subagent finished 
 Fixed PushNotification saying a push was not sent in claude remote-control sessions right after a phone message, without the /config toggle, or when started from inside Claude Code 
 Fixed files sent from remote sessions being refused as "could not be vouched for" when more than 256 were sent at once 
 Fixed a rare failure to load managed settings at startup right after a login refresh 
 Fixed /tui exiting without a message, or with a raw system error, when Claude Code could not be started again 
 Fixed a link address shown as text being hidden by a colour or conceal style a reply left on, including where it wraps in a table or a question preview 
 Fixed Fable models listed in availableModels not appearing in the /model picker for sessions signed in to a Claude apps gateway; such a model now shows its built-in row in place of a modelPicker row added for the same model 
 Fixed the Claude apps gateway's admin spend view showing a developer's old groups and group cap after their session stopped carrying groups 
 Fixed CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC hiding the Claude apps gateway spend limit in /usage and the status line. The spend limit request goes to the gateway the session is signed in to 
 Fixed subagents in their own linked worktree being shown the parent session's git branch, status and recent commits 
 Fixed Claude stopping at the end of the current tool when text typed in the prompt cancelled backgrounding with ← ; Claude now keeps working in the foreground 
 Fixed --tools and --restricted not applying to built-in tools that register after launch, and deprecated tool names reaching tools outside the caller's tool set 
 Fixed an interrupt not ending the turn until a timeout while Claude waited for an MCP server's resource list 
 Fixed a mod's hook being handed a deeply nested tool input cut short with no error, so a guard could pass content it never saw 
 Fixed Esc not stopping a self-paced /loop that was moved to the background with ← ; cancelling a pending wakeup now shows a notice 
 Fixed commands and hooks in background sessions inheriting FORCE_COLOR=3 , which put color escape codes into the output Claude reads 
 Fixed claude agents starting a new background service as it exited when both were stopped with a session open (for example at a reboot), which could delay shutdown and restart an interrupted session 
 Fixed a custom agent named worker being shown as "Agent" in auto-mode denial notices and in the activity lists of task detail views 
 Fixed Bash permission checks for for-loops over glob patterns, improving permission-check accuracy 
 Fixed forked skills invoked from Workflow subagents delivering their results to the main conversation instead of the invoking agent 
 Fixed in-process agent teammates failing their first SendMessage call until they loaded the tool through tool search 
 Fixed Claude being told on resume that an unfinished background workflow may have been stopped by TaskStop , which can never be the cause 
 Fixed Claude not being told when you stop a long-running MCP tool call from the tasks panel or a connected client 
 Fixed a background session's /loop stopping without notice when its next wakeup came due while the session's process was down; the session now says so and Claude is told 
 Fixed raw terminal hyperlink bytes in a reply or a teammate's message being drawn as a clickable link with a hidden address 
 Fixed plugin marketplaces whose repository has large git submodules failing to add or refresh: only the submodules that hold plugin files are now fetched 
 Fixed the /advisor dialog showing a checkmark on a saved advisor model that is no longer available; it now opens on "No advisor" 
 Fixed the notification for an MCP tool call that moved to the background showing a shortened task id 
 Fixed vim mode's ~ moving the cursor past the last character of a line, so x after it did nothing, and 3~ running on into the next line 
 Fixed the cursor landing one character too far after pasting accented text copied from macOS (such as a file name) into the middle of the prompt 
 Fixed the terminal freezing, with ctrl+c ignored, when a response ran to tens of thousands of lines 
 Fixed calls a mod makes while it reloads during a plugin hooks worker restart getting past another mod's guard hook that has a .catch ; such calls are now refused 
 Fixed plugins whose hooks module nests code thousands of levels deep failing to load or validate with a bare stack-overflow message 
 Fixed claude plugin test passing a session.append hook that removes tool call, tool result or thinking blocks that a real session keeps 
 Fixed Claude not being told it can resume background subagents with SendMessage after a session was killed and resumed a second time 
 Fixed a file being treated as already read after a Bash command such as cat ran without printing it 
 Fixed plugin options named constructor or prototype always reading as their default and never reloading the plugin when edited 
 Fixed a mod's hot reload missing a save made while /reload-plugins or session start was reading the mod's files 
 Fixed the mod hot-reloading question being asked again every turn for the whole session when it is approved without picking an answer 
 Fixed /model , /fast and /output-style saving their setting without asking a plugin's config.set hook 
 Fixed bold text being drawn faint in piped output when it directly follows dim text 
 Fixed replies whose quotes nest deeper every few lines freezing the terminal for seconds and using gigabytes of memory 
 Fixed a mod's hot reload missing a save made within a few milliseconds of its last reload, which left the mod on its old version until the next save 
 Fixed claude mcp serve background Bash results not naming the output file, and its tool description promising a notification that never arrives 
 Fixed an async SessionStart hook's unchanged context being added to the conversation again on every resume 
 Fixed variables a SessionStart hook writes to CLAUDE_ENV_FILE not reaching the Bash tool after an in-app /resume or /branch 
 Fixed a skill's allowed-tools and effort being dropped when the Skill tool finished before the response stream ended, which denied the skill's Bash commands in -p runs 
 Fixed a tampered cache of server-managed settings making a person's own plugin count as organization-managed on machines whose managed settings list or enable plugins 
 Fixed Claude 3 Opus and Claude 3.x Sonnet sessions being offered tool search, which those models reject, where feature flags are unavailable 
 Fixed generated type files being written into a --plugin-dir plugin's folder in -p and SDK sessions; they are now written only where a mod is being developed 
 Fixed text with tabs or bidirectional control characters losing its end at the edge of the screen or drawing over nearby rows 
 Fixed /model saying a Max effort pick was saved as your default for new sessions; Max applies to the current session only 
 Fixed an async hook's JSON output being ignored when it is printed over several lines 
 Fixed the Read tool rejecting calls with an empty pages parameter instead of treating it as omitted 
 Fixed project-scope plugins not loading in VS Code on Windows due to drive-letter casing ( #74612 ) 
 Fixed plugin install and uninstall at project or local scope on Windows missing the install record, or adding a second one, when only the drive letter's case differs 
 Fixed a queued message being lost when pulled back into the prompt with ↑ or Esc just after ← : prompt history now keeps it 
 Fixed mod hot-reloading turning off for the whole session when an SDK host closed its enable question before anyone answered; the question is now asked up to three times 
 Fixed a prompt that a mod's prompt.submit hook rewrote or dropped still being saved as typed to prompt history and to the transcript's queued-prompt records 
 Fixed non-interactive sessions telling you about MCP servers that need authentication when your request doesn't use them 
 Fixed the claude_code.auth OpenTelemetry login event not being 

[... truncated for safety ...]