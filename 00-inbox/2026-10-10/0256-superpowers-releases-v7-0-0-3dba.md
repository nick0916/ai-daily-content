---
id: inbox_454d9754
source: superpowers-releases
source_type: rss
url: "https://github.com/obra/superpowers/releases/tag/v7.0.0"
author: "obra"
published_at: 2026-10-10T00:28:58+00:00
fetched_at: 2026-10-18T02:56:56.725618+00:00
content_hash: "3dbace8ae7c987833b66e84b612324894f481c040b72437d270e5e65e9886655"
lang: en
caption_quality: None
raw: true
topics: []
---

# v7.0.0

We rebuilt brainstorming from scratch so it does a much better job of what it was always for: helping you work out what you actually want and put it into words before anything gets built. The new skill asks you to describe what you're after and why, plays back what it heard so you can correct it, and keeps asking good questions until the picture is clear. Then it matches the process to the work, from just doing it to writing a full design. 
 This release also adds a native plugin manifest for the Antigravity Marketplace and fixes Windows hook discovery, Git Bash paths, Hermes skill descriptions, and several smaller bugs. 
 Brainstorming 
 
 Brainstorming draws out what you want before it proposes anything. Its first message offers to skip the questions and asks one open question about a real moment or a concrete picture. It offers a menu only when you're stuck. Along the way, it offers to look at prior art, your project, or the web. As it understands each part, it plays that part back in a few hundred words and marks its guesses as guesses. ( #2463 ) 
 It sizes the work after it understands what you want, and says so in plain words. It does a quick, clear task right away, agrees a small change with you in chat, and writes a design document for a project. You can override its call, and it steps up a size if the work grows. ( #2463 ) 
 A builder check replaces the spec-document reviewer. A fresh subagent reads the design as the person who'll build it and lists what they'd still need to ask. Brainstorming answers what it can, makes the minor calls itself and marks them as its own, and brings you the questions that change what gets built, in one round. ( #2463 ) 
 It finds out which choices about how the thing gets made you want to own. Platform, language, libraries, medium: if you have strong views, it talks them through; if you hand them over, it picks sensible defaults and tells you what it picked. It does this even when you skip the questions. We made this change after a session designed an iOS app, never asked about platform, and built a web app. ( #2482 , #2483 ) 
 It offers the visual companion whenever seeing would help more than reading: screens, layouts, flows, options that look different, diagrams. The offer drops its token-cost warning. ( #2463 ) 
 The visual companion now shows screens containing $' , $&amp; , and similar sequences intact. The server inserted content with String.replace , which treats those sequences as replacement patterns. It now inserts content literally. Thanks @andrew-yian for the report and @luochen211 for the fix. ( #2362 , #2364 ) 
 
 Antigravity 
 
 agy plugin install https://github.com/obra/superpowers now installs Superpowers as a native Antigravity plugin. We added .antigravity-plugin/plugin.json with the Marketplace display name, logo, and suggested prompts. Previously, agy fell back to importing the repo as a Gemini CLI extension, then rejected the copied Claude-format hooks file on every session with invalid hook "hooks": command hook must specify 'command' . The install command stays the same. ( #2479 ) 
 Superpowers bootstraps on Antigravity through skill discovery. Antigravity has no session-start hook event, but it shows the model each installed skill's description, and using-superpowers ' "Use when starting any conversation" prompts the model to load it. We verified this on agy 1.3.1 across 12 runs: "Let's make a react todo list" and "add a settings page" triggered brainstorming before any code, and a failing test triggered systematic-debugging before any edit. We also corrected the README and porting guide, which described a session-start hook and install script that never existed. ( #2479 ) 
 
 Hooks 
 
 SessionStart now works when the harness launches it with a broken PATH . The hooks no longer look up dirname , cat , or bash on PATH , so a startup PATH that can't resolve them ( anthropics/claude-code#43127 ) no longer drops the bootstrap. Thanks @kannan983 for the report and Ada Sen for the fix. ( #2310 , #2349 ) 
 Windows: run-hook.cmd finds per-user Git for Windows installs and skips WSL launchers. It now checks %LOCALAPPDATA%\Programs\Git , and when it searches PATH , it skips the WSL bash.exe launchers, which fail without a Linux distro. Thanks @jp5247 for the report, and @citizen204 ( #1864 ) and @KaiyiQuan ( #2365 ) for the fixes we combined here. ( #1863 , #2393 ) 
 Windows: run-hook.cmd ignores bash and where in the current directory. Previously, a repository could plant bash.cmd or where.bat and have it run at session start. ( #2393 ) 
 Windows: run-hook.cmd now passes hook exit codes to the harness. It used to report success even when the hook failed. ( #2393 ) 
 
 Subagent-Driven Development 
 
 sdd-workspace leaves a repo's own .superpowers/sdd/.gitignore alone. It used to overwrite the file with * on every run, reverting any version a repo committed (for example, to track progress.md ledgers). It now writes the default only when no file exists. Thanks @aruizcu1989 for the fix. ( #2161 , #2399 ) 
 Plan markers stay repo-relative on Windows. On Git Bash, sdd-workspace compared git rev-parse 's C:/... root with the plan's /c/... path, so every workspace marker recorded an absolute, machine-specific path. It now resolves the root the same way as the plan path. We found this while landing @t0domanh 's Windows test fixes ( #2149 ). 
 
 Executing Plans 
 
 task-done now records tasks whose test command passes silently. When a passing command printed nothing, task-done exited 1 without writing the ledger line, so a finished task looked unfinished. It now records → (no output) . Thanks @KenM-BT for the report and Ada Sen for the fix. ( #2385 , #2388 ) 
 
 Requesting Code Review 
 
 The example's base-SHA command survives skill arguments. Claude Code replaces $1 in a skill body with the second argument word, so invoking the skill with arguments turned awk '{print $1}' into awk '{print &lt;word&gt;}' . The example now uses cut -d' ' -f1 , which contains no $ . Thanks @errmakov for the report and @klemens-floege for the fix. ( #2311 , #2361 ) 
 
 Systematic Debugging 
 
 The multi-layer diagnostic example no longer prints the secret it checks for. ${IDENTITY:+SET}${IDENTITY:-UNSET} and env | grep IDENTITY both echoed the signing identity's value into logs. The example now reports only whether the variable is set. Thanks @kennyg-g for the report and @m2dumpling for the fix. ( #2375 , #2380 ) 
 
 Hermes Agent 
 
 Hermes' skill list now shows Superpowers skill descriptions. Hermes lists each plugin skill with the description passed to register_skill , which defaults to empty. The plugin passed only a name and path, so every skill appeared blank and the model had nothing to choose from. The plugin now passes each skill's frontmatter description. Thanks @pepijn-blom for the fix. ( #2284 )