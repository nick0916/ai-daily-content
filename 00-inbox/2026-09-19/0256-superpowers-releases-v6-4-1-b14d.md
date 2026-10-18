---
id: inbox_1f556877
source: superpowers-releases
source_type: rss
url: "https://github.com/obra/superpowers/releases/tag/v6.4.1"
author: "obra"
published_at: 2026-09-19T00:32:44+00:00
fetched_at: 2026-10-18T02:56:56.727037+00:00
content_hash: "b14dfaecc16fd55dec38983b23f97a6210693af5f92572569b87473a6c254b4f"
lang: en
caption_quality: None
raw: true
topics: []
---

# v6.4.1

v6.4.0 was never shipped. v6.4.1 is the first release with these changes. It holds back the new proving-it-works-with-a-movie skill, which is getting cleanup and robustness work and will return in a later release. 
 The new diagnosing-superpowers skill figures out what went wrong in a session. executing-plans is rebuilt as Native execution, a cheaper alternative to subagent-driven development. This release also adds support for three new harnesses: OpenCode 2.0, Muse, and Qwen Code. 
 New Skills 
 
 diagnosing-superpowers : when a session goes wrong (repeated work, an ignored plan, a skill that didn't fire, a surprising bill), ask your agent to "figure out what went wrong with superpowers in this session." It pins down the problem with you, reads the transcripts on disk, and reports what happened with path:line evidence for every finding. On request it builds a scrubbed bundle or drafts a GitHub issue for your approval, with the cited evidence left intact. Works on the current session or a past one. ( #2236 , #2287 ) 
 
 Executing Plans 
 Heads up: executing-plans no longer stops every few tasks to check in with you. It runs the whole plan, then gets one review at the end. 
 
 Native (inline) execution is now a real mode. executing-plans was a 64-line stub that measured the same as running with no plugin at all. It is rebuilt: the session implements every task itself under the same workspace, ledger, and stopping rules as subagent-driven development, then dispatches one fresh whole-branch review on the most capable model. task-start and task-done helpers keep the ledger and test log honest. It is the cheapest way to run a plan and runs well on a mid-tier session model. ( #2318 ) 
 The plan handoff offers two approaches, Subagent-driven and Native, says what each costs, and recommends one for this plan with a reason drawn from the plan. If you already chose one, it keeps your choice. ( #2258 , #2318 ) 
 
 Writing Plans 
 
 You review the saved plan before anything runs. Approving an idea or a scope no longer counts as approving a plan you haven't seen. ( #2258 ) 
 Plans carry a Review Focus section : up to five inputs or failure modes the spec implies but no task's tests exercise, each pinned by a test in the task that owns the code. In evals, every implementer shipped the same crash on an input the spec implied but never named; this section exists to catch that. ( #2319 ) 
 
 Brainstorming 
 
 Brainstorming finds out why you want the thing before proposing features, reflects your intent back for correction, and ties your approval to the actual design and planning stages. The motivating session took "that scope is ok" as permission to scaffold. ( #2258 ) 
 
 Code Review 
 
 Reviewers judge behavior the spec doesn't mention by what a reasonable user would expect, so a crash on an unnamed input no longer slides through as Minor. A "Declined to judge" list shows what the reviewer skipped, and the session running the plan decides each one. ( #2319 ) 
 The multi-commit BASE_SHA alternative is now git merge-base origin/main HEAD . A bare origin/main showed main's newer files as phantom deletions once main moved past the branch point. ( #2133 , #2118 ) 
 
 Test-Driven Development 
 
 The project's suite defines green, not just your test file. When a task named one test file, sessions ran only that file in 11 of 12 probe runs, so a broken test next door went unseen. The skill now says to run the project's test command and report every failure by name, including ones you didn't cause. ( #2110 ) 
 
 Subagent-Driven Development 
 
 Plans with the same basename no longer share a workspace. docs/alpha/plan.md and docs/beta/plan.md resolved to one directory and task-brief silently overwrote the other plan's brief. Each workspace now records its owning plan; a collision gets its own directory. Existing workspaces are adopted in place. ( #2138 , #2045 ) 
 review-package rejects empty or non-descendant BASE..HEAD ranges (exit 3), so an implementer that committed to the wrong branch can't produce a "clean" review of nothing. ( #2136 , #2050 ) 
 On Claude Code, the controller can run one layer down, as a nested subagent on a mid-tier model. It measured about half the cost and wall clock. It's opt-in: ask for it, or tell your agent your session model is too expensive to spend on coordination. ( #2320 ) 
 
 New Harness Support 
 
 OpenCode 2.0.4+ is supported alongside V1. Skills register through V2's native API, and the bootstrap survives continuation, restart, forks, and compaction. Delegated child sessions no longer receive the controller's bootstrap. ( #2106 , #2306 ) 
 Muse : native plugin manifest and SessionStart hook. muse plugins install ./ then muse plugins approve superpowers . ( #2317 ) 
 Qwen Code added to the install docs: qwen extensions install obra/superpowers . ( #2132 ) 
 
 Fixes 
 
 Skills work when a packager strips executable bits. The Codex marketplace and MiniMax Code's repackage both shipped our scripts non-executable, so every documented command failed with Permission denied . Skill prose now invokes bundled scripts through their interpreter ( bash scripts/foo.sh , node render-graphs.js ), and the SDD helpers call each other the same way. ( #2301 , #2134 , #2040 ) 
 The platform-support issue template applies a label that exists ( new-harness ). ( #2250 ) 
 
 Documentation 
 
 docs/testing.md describes the Quorum eval lab, replacing stale Drill references and commands. ( #2135 ) 
 README: a "When Something Goes Wrong" section pointing at diagnosing-superpowers . 
 AGENTS.md is now the canonical contributor guidelines. CLAUDE.md is a one-line reference to it. AGENTS.md used to be a symlink to CLAUDE.md , which Muse's installer rejects. ( #2317 ) 
 Adopted the Prime Radiant Community Code of Conduct. ( #2122 )