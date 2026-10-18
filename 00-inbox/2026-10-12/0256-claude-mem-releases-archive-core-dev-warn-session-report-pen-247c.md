---
id: inbox_43f4e9ca
source: claude-mem-releases
source_type: rss
url: "https://github.com/thedotmack/claude-mem/releases/tag/archive%2Fcore-dev"
author: "Boulea7"
published_at: 2026-10-12T05:42:04+00:00
fetched_at: 2026-10-18T02:56:55.893928+00:00
content_hash: "247c1e5d03f6f45685864818139a1030b286dfd9ef5633e703f9ea748f45216c"
lang: en
caption_quality: None
raw: true
topics: []
---

# archive/core-dev: warn(session): report pending buffer counts during teardown (#4614)

fix(installer): select installed agents before offering Claude Code 
 
 Preselect detected agents and ask to install Claude Code only if the user selects it. Keep Claude Code as the fallback when no supported agent is detected. 
 
 fix(integrations): close DSH dependency graph and preserve profile cleanup 
 
 Bundle the pinned pure SDK helpers with provenance and retained licenses so Bun installs do not resolve unpublished host peer packages. Keep DSH profile ownership recoverable and uninstall the native plugin before removing its package files. 
 Validate the standalone host contract, successful profile add/remove, failure rollback, and configured watch preservation. 
 
 test(integrations): isolate DSH CLI fixtures from release builds 
 
 Run profile commands in a fresh process with a temporary data directory and package fixture. This makes the add/remove and rollback tests independent of generated release output and module-level path caches. 
 
 perf(observer): send session_id and trace on OpenRouter requests ( #4418 ) 
 
 Observer requests that reach OpenRouter (openrouter.ai, or the cmem.ai 
gateway, which spreads the client body into its upstream request) now carry: 
 
 session_id: a one-way SHA-256 of the observed session's id, stable for the 
whole Claude Code session. OpenRouter uses it as the sticky-routing key, so 
a session stays on the provider that holds its prompt cache. Broadcast maps 
it to PostHog's $ai_session_id. 
 trace.trace_id: a random UUID per observer generation, minted in 
openObserverGeneration, so it changes whenever the conversation is 
recycled or restarted ($ai_trace_id). 
 trace.trace_name 'claude-mem observer', trace.generation_name the request 
kind (init, observation, summary, field_compression, telegram_wrapup; 
$ai_span_name) and trace.claude_mem_version, the build-stamped plugin 
version (metadata_claude_mem_version). 
 
 The session id is derived, not stored, because the ActiveSession object 
does not live as long as the session: an idle generator drops it after three 
minutes and the next tool call builds a new one. No user field is sent; the 
gateway sets it server-side. Custom base URLs behind the OpenRouter provider 
and the openai-compatible presets get neither field. 
 Claude-Session: https://claude.ai/code/session_011rgzkjwPRzo2YH57oEFpaP 
 Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 perf(observer): open init and continuation prompts with the same fixed instructions ( #4415 ) 
 
 
 perf(observer): open init and continuation prompts with the same fixed instructions 
 
 
 A provider prompt cache (OpenRouter, the cmem.ai gateway) hits only on a 
byte-identical prefix. The init prompt put the per-generation 
session-start context, whose first line is "# [project] recent context, 
", right after system_identity and ahead of ~6.9k chars 
(~1.7k tokens) of fixed instructions. The continuation prompt opened 
with its greeting and that same context. No two sessions shared more 
than system_identity, and an init and a continuation shared nothing. 
 Both prompts now open with one block that depends on the mode alone: 
system_identity, observer_role, spatial_awareness, recording_focus, 
skip_guidance and the observation schema. The prior context, the 
user's request, the continuation greeting and continuation_instruction 
follow it, and the MEMORY PROCESSING header stays last. Every piece of 
text is unchanged; only its position moved. For the code mode the 
shared start of two sessions' system messages grows from 422 chars 
(init vs init) and 0 (init vs continuation) to ~7.26k chars. 
 The Claude SDK and Codex paths use the same builders, so their first 
user message opens with the same block. Nothing reads the prompt's 
order: the request block is found by regex and history pruning keys on 
&lt;user_request&gt;. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_011rgzkjwPRzo2YH57oEFpaP 
 
 fix(modes): point continuation_instruction at the schema above it 
 
 The previous commit moved the observation schema into the fixed block 
that now opens every continuation prompt, so continuation_instruction 
follows the schema instead of preceding it. Its "using the XML 
structure below" now reads "above" in all 33 modes that carry it: 
code, law-study, email-investigation, meme-tokens and the 29 code 
language variants, which reuse the English sentence and append a 
LANGUAGE REQUIREMENTS line. Nothing else in those files changes. 
 The other position words in the mode prompts and in src/sdk/prompts.ts 
still point the right way and stay as they are: the footer's "XML 
structure above" and output_format_header's "this XML structure" sit 
inside the schema next to the XML they name; "The context above" in 
the prior-context wrapper refers to the block directly above it; the 
observation prompt's "block above" and the summary prompt's "XML 
structure above" belong to prompts this change does not reorder; and 
"earlier in this session", "prior messages in this conversation" and 
"previous reply" refer to time, not position. 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_011rgzkjwPRzo2YH57oEFpaP 
 
 Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 chore: bump version to 13.30.0 
 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_011rgzkjwPRzo2YH57oEFpaP 
 
 docs: update CHANGELOG.md for v13.30.0 
 
 Co-Authored-By: Claude Opus 5.5 noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_011rgzkjwPRzo2YH57oEFpaP 
 
 docs(version-bump): the agent publishes to npm with the monthly token ( #4371 ) 
 
 The "human handoff" npm step was obsolete. Agents publish with a 30-day 
granular token in the maintainer's ~/.npmrc. When it expires, open the npm 
new-token page and ~/.npmrc for the maintainer instead of hunting backups or 
waiting on the npm-publish workflow, whose NPM_TOKEN secret has failed every 
tag since v13.26.1. 
 Claude-Session: https://claude.ai/code/session_013fww8bJwhSZFgYhfXs6GZm 
 Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(hooks): skip timeline injection on Claude Code resume ( #4423 ) 
 
 
 chore: bump version to 13.30.1 
 
 
 docs: update CHANGELOG.md for v13.30.1 
 
 
 perf(session-start): newest-N per project key, local-first context ( #4427 ) 
 
 
 SessionStart read every observation and summary of the project family 
(~21.7k rows / 63 MB on a 1.2 GB db) and sorted them to keep 50, because 
 project IN (...) OR merged_into_project IN (...) cannot stop early. Cold 
pages made that 0.8-1.7 s per session start. 
 
 v63: (key COLLATE NOCASE, created_at_epoch DESC) indexes on observations 
and session_summaries for project and merged_into_project. 
 queryObservationsNewest / querySummariesMulti take the newest N per 
(column, key) and keep the newest N of the union. Same rows, same order 
(verified on a real 1.2 GB db); 3.8 ms instead of 0.05-1.7 s. 
 The worker no longer waits on a sync pull before rendering SessionStart 
context; it only nudges one in the background. 
 Precomputed SessionStart context is servable with cloud sync on. The local 
db is the source of truth and every op sync applies invalidates the files, 
so the files no longer wait on a Realtime channel the hub may not offer. 
 cowork hook: no cmem.ai context read (SessionStart or agent prompts) on a 
machine with a local claude-mem install. 
 
 Claude-Session: https://claude.ai/code/session_011rgzkjwPRzo2YH57oEFpaP 
 Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(sync): preserve Retry-After minimum after jitter ( #4383 ) 
 
 
 fix(sync): preserve hub retry minimum after jitter 
 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Rebuild shipped source maps with checkout-local dependencies 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
Co-authored-by: Alex Newman thedotmack@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(logs): stop tail reads at the existing byte limit ( #4393 ) 
 
 
 fix(logs): stop tail reads at the existing byte limit 
 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 build: regenerate portable worker source maps 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
Co-authored-by: Alex Newman thedotmack@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(sse): remove clients when Bun closes their socket ( #4394 ) 
 
 
 fix(sse): remove clients when Bun closes their socket 
 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 build: regenerate portable worker source maps 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
Co-authored-by: Alex Newman thedotmack@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(viewer): release loading after a failed pagination request ( #4387 ) 
 
 
 fix(viewer): release pagination loading after a failed page 
 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 fix(viewer): retain successful pages and expose manual recovery 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 build(viewer): ship pagination recovery with current dependencies 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 fix(viewer): scope pagination failures to the active feed 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 build: refresh viewer bundle for scoped failure handling 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
Co-authored-by: Alex Newman thedotmack@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(worker): preserve observation context during field compression ( #4403 ) 
 
 
 fix(worker): freeze observation context before field compression 
 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 build: ship observation compression context correction 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
Co-authored-by: Alex Newman thedotmack@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(smart-read): include generator functions in native outlines ( #4419 ) 
 
 
 fix(parser): retain JavaScript and TypeScript generator declarations 
 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 build: refresh generator-aware smart outline MCP artifact 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
Co-authored-by: Alex Newman thedotmack@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(smart-read): preserve lexical ownership of outline symbols ( #4406 ) 
 
 
 fix(smart-read): assign symbols to their nearest lexical container 
 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 build: ship corrected smart-outline symbol ownership 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
 
 Signed-off-by: Rudy Celekli 47457359+rudycelekli@users.noreply.github.com 
Co-authored-by: Alex Newman thedotmack@gmail.com 
Co-authored-by: Claude Opus 5.5 noreply@anthropic.com 
 
 
 fix(smart-read): retain complete multiline imports in outlines ( #4409 ) 
 
 
 fix(smart-read): preserve complete import capture ranges 
 
 
 Si

[... truncated for safety ...]