---
id: inbox_aa05907b
source: claude-code-releases
source_type: rss
url: "https://github.com/anthropics/claude-code/releases/tag/v2.1.299"
author: "ashwin-ant"
published_at: 2026-10-14T02:49:42+00:00
fetched_at: 2026-10-18T02:56:31.153244+00:00
content_hash: "b90721ea4a088bfbaf60fb168a96597a308e8e11198c62829b0c1dfeede914eb"
lang: en
caption_quality: None
raw: true
topics: []
---

# v2.1.299

What's changed 
 
 Added CLAUDE_CODE_DISABLE_FILE_MENTIONS environment variable: Claude gets the paths of @ file mentions to read with its file tools, not the files' contents 
 Added idle compaction in the terminal: a 200K+ token conversation left idle for about 54 minutes is compacted before its one-hour prompt cache expires, so your next message doesn't reprocess it all 
 Added CLAUDE_CODE_IDLE_COMPACT_MIN_TOKENS to change idle compaction's 200K-token minimum; "idleCompaction": false in settings.json turns it off. Both need v2.1.290 or later 
 Added $.prompt.media so a prompt.submit hook of a mod installed by managed settings can read the bytes of an image or document attached to the prompt 
 Added $.session.identity() for mods installed by managed settings: how the session is signed in, and its organization and email when managed forceLoginOrgUUID lists that organization 
 Added size , weight , mono and tabular to a mod's Text and named spacing steps ( xs to xl ) to its Box ; bold is deprecated in favor of weight 
 Added --shutdown-drain-sec to claude self-hosted-runner orchestrator : on SIGTERM it stops polling and gives the poll in flight and running spawn hooks up to that many seconds to finish 
 Added the skill's frontmatter, source, plugin name and file path to what a mod's skill.prompt hook receives 
 Added /effort and /fast in agent view to set what new sessions start with; a bare /model , /effort or /fast there now opens a picker 
 Added a "safe mode" line to the agents view peek panel for background sessions started with --safe-mode 
 Added a one-time note when plan mode won't ask before most edits or commands because bypass permissions is available 
 Added --disallow-tools and a disallowed_tools case field to claude plugin eval to keep specific built-in tools, such as Agent, out of eval runs 
 Added support for turning off the attribution block in Claude Desktop's Code tab: set CLAUDE_CODE_ATTRIBUTION_HEADER=0 in the env of a Claude apps gateway's code policy 
 Added a field to the attribution block in Claude Code sessions behind a Claude apps gateway; remove the block with CLAUDE_CODE_ATTRIBUTION_HEADER=0 
 Added a queue door to the session.append mod hook, so a mod can make the transcript's queue records differ from the prompt as sent 
 Added a note in /plugin and claude plugin validate naming a mod's hooks that are skipped where an organization manages Claude Code 
 Added /usage warnings for max effort, workflows, always-on context and large tool results 
 Fixed the error for a denied cloud session, which could point to the wrong organization when a key from apiKeyHelper was in use 
 Fixed sessions on a gateway-specific model name behind a custom ANTHROPIC_BASE_URL ending with "Prompt is too long · automatic compaction failed" near 200K tokens instead of sending the request 
 Fixed a mod that submits a prompt at the end of every turn keeping a headless run going past --max-turns , --max-budget-usd , an interrupt, or the end of the host's conversation 
 Fixed cloud sessions sometimes showing the model's follow-up text after a tool group's one-line label 
 Fixed the Write and Edit tools creating a mod in a session's mods folder without asking in accept-edits mode when the config directory's path has no .claude in it 
 Fixed installed mods that kept running in an open session after being turned off remotely; they now unload between turns 
 Fixed Edit and Retry in Cowork and claude.ai cloud sessions failing on a message stopped while its UserPromptSubmit or mod prompt.submit hooks were still running (regression in 2.1.296) 
 Fixed an agent teammate started without a description keeping part of a credential from its prompt in the task description shown for it 
 Fixed the claude.ai view of a Remote Control or cloud session freezing when a large batch of events could not finish uploading over a slow connection 
 Fixed a sandboxed shell command being able to write into a --plugin-dir folder, whose code Claude Code reloads and runs outside the sandbox 
 Fixed memory growth under heavy debug logging ( --debug , --debug-file ), and a hang on exit when the debug log is on a disk or network mount that stops accepting writes 
 Fixed memory growing without bound when debug output goes to stderr and the parent process stops reading it 
 Fixed rm prompts on shell -c scripts that don't run rm . An rm built at run time in a script Claude Code can't read no longer prompts unless CLAUDE_CODE_STRICT_INLINE_SHELL_RM_PROMPT=1 
 Fixed double-clicking a word in an expanded transcript row in fullscreen mode collapsing the row instead of selecting the word 
 Fixed claude mcp list , claude doctor and /status reporting an empty .mcp.json as invalid 
 Fixed /btw jumping the transcript to the bottom when asked while scrolled up in fullscreen 
 Fixed sandboxed commands failing on WSL2 with bwrap: Can't mkdir /mnt/c/Program Files/ClaudeCode when the sandbox can write to the Windows drive 
 Fixed scheduled wakeups (ScheduleWakeup) not firing while a background task was running in Agent SDK, IDE and claude remote-control sessions 
 Fixed a mod's prompt.submit rewrite being silently dropped, sending the prompt as typed, for some prompts with a pasted image or an image that can't be read 
 Fixed a Remote Control prompt being lost when another queued prompt in the same batch failed to deliver 
 Fixed a Remote Control prompt that had passed its hooks being dropped from prompt history when Stop interrupted the next queued prompt's hook 
 Fixed sign-in, MCP servers and project trust appearing lost on Linux after a sandboxed command left an empty .config.json in the config directory 
 Fixed /sandbox reporting success when its setting could not be saved because the project folder is not writable; it now says nothing changed and why 
 Fixed SDK and headless sessions staying in auto mode after the host switched to a model that doesn't support auto mode 
 Fixed MCP servers named constructor or prototype in an MCP config never being connected 
 Fixed tools of an MCP server named constructor or toString asking for permission in auto mode and bypass permissions mode 
 Fixed a spurious "synced[0] commands path not found" plugin error at startup when another Claude Code process had just updated a claude.ai-synced plugin 
 Fixed the Artifact tool advising a retry when a publish that requests connectors or other access was refused by the server or a proxy (HTTP 403); it now says so and what to tell the user 
 Fixed Cowork cloud sessions staying on an old account plugin after a plugin reload that timed out or a restart that reused a recent sync 
 Fixed document blocks being dropped from your own message sent while Claude is working 
 Fixed Claude in Chrome asking for permission while no browser is connected; it now says the extension is not connected 
 Fixed the fullscreen "Update installed" notice being hidden behind the idle "/clear to save tokens" hint; it now shows beside the hint 
 Fixed a mod hook, with or without a .catch , being run again without end when it waits on another mod's noun that does its work outside the call 
 Fixed the Claude apps gateway serving models that a policy's availableModelsMatch: exact or deniedModels blocks; it now answers 400 and leaves them out of its model lists 
 Fixed the server-managed settings request to Anthropic carrying a third-party gateway's API key when a managed settings file sets ANTHROPIC_BASE_URL 
 Fixed streams through a custom ANTHROPIC_BASE_URL being aborted after 180 seconds with no data arriving; they now wait 300 seconds, whether or not feature flags are loaded 
 Fixed a mod's tool.describe or prompt.section answer that changed after $.ui.invalidate never reaching Claude; the new answer is now sent on the next turn 
 Fixed a settings file being ignored when enabledMcpjsonServers or disabledMcpjsonServers held a single server name (letters, digits, - or _) as a plain string 
 Fixed claude plugin test pausing a hook's time budget while a served $ method it had called kept making $ calls after answering 
 Fixed high memory use after resuming a cloud or Remote Control session that had run many subagents 
 Fixed plugin hooks being skipped when they pass a very deeply nested tool input or message on with next() 
 Fixed a value a mod's hook passes to next() , returns, or sends to a $ method being refused whole when one of its getters throws a RangeError ; now only that key is refused 
 Fixed /usage , the approaching-limit warning (terminal and VS Code) and the status line sometimes showing more than 100% used ( #92238 ) 
 Fixed wrapped text mixing CJK or emoji with Latin words losing its last line or leaving a blank row at some terminal widths 
 Fixed a cloud session sometimes ignoring the answer to a permission prompt or a question when the answer was given while the session's worker was being replaced 
 Fixed bold, italic and other nested text styles running over table borders or being lost on wrapped rows 
 Fixed Cowork cloud sessions running the old version of an account plugin changed, removed or disabled from another device until the session restarted 
 Fixed deny and ask rules for an MCP server ( mcp__&lt;server&gt; ) not applying when the server's normalized name contains a double underscore 
 Fixed long conversations losing newly attached images on every turn after one oversized image was refused by the API 
 Fixed the plugin_loaded telemetry event reporting has_hooks as false for plugins whose hooks are a hooks module, built-in plugins included 
 Fixed images attached while Claude is working (VS Code, desktop app, SDK) being sent at full size, which led to repeated image errors in long conversations 
 Fixed the image coordinate hint being missing or slightly off for large near-square images on newer models 
 Fixed feature flag, startup, fast mode, profile and feedback requests to Anthropic carrying the API key configured for a third-party gateway ( ANTHROPIC_BASE_URL ); Anthropic API keys are still sent 
 Fixed a mod's hot reload ignoring a fix saved right after a failed reload; saving a mod file without changing it no longer reloads the mod 
 Fixed mods loaded from source files being refused when a hook hands $ to a function declaration imported from another file of the mod 
 Fixed a regression in 2.1.296 where cloud and headless sessions could run an approved tool call twice if a new message arrived as the session resumed after a restart 
 Fixed scheduled tasks being announced for the wrong minute: the scheduling tools now report each job's actual next run time 
 Fixed mods' hooks being handed values with __proto__ keys silently removed, which could skip a tool.check guard on a tool call another mod made 
 Fixed claude -p saying nothing when a settings file fails validation: text-output runs now list the file and the invalid entry on stderr 
 Fixed long pastes in terminals without bracketed paste losing all text after an invisible control character, such as a mis-decoded curly quote 
 Fixed managed settings and organization policy not being fetched when the stored login's plan was changed locally on machines whose MDM or managed-settings file sets forceLoginOrgUUID 
 Fixed MCP connections over HTTP hanging for 30 seconds and failing when a server never ends the body of its reply to a notification ( #99014 ) 
 Fixed MCP servers added to a running headless or SDK session being connected before some policy checks ran; a blocked server is now reported as failed without being contacted 
 Fixed claude mcp list , claude mcp get and subagent MCP servers starting a server that a policy check blocks; it is now reported as blocked without being started 
 Fixed /reload-plugins not loading a plugin installed from another terminal a moment earlier 
 Fixed blank rows appearing under CJK and emoji text squeezed into a one-cell column, as in a very narrow terminal 
 Fixed text cut in the middle beside wide characters leaving a cell unused or being cut twice, and a

[... truncated for safety ...]