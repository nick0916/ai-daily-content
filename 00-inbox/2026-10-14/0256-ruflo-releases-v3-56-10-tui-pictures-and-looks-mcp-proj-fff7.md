---
id: inbox_13e9e654
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.56.10"
author: "ruvnet"
published_at: 2026-10-14T16:33:28+00:00
fetched_at: 2026-10-18T02:56:54.657094+00:00
content_hash: "fff75925748d5700df4f66befac9223185d0b36174e48fa4a108e80c64d56f57"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.56.10 — TUI pictures and looks, MCP project cwd and daemon fixes, memory and analyze fixes

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.10 (latest, alpha, v3alpha). The CLI pins @claude-flow/memory 3.0.5 ( #4183 ) and @claude-flow/cli-core 3.7.3 ( #3987 ), both published earlier, plus shared 3.0.5, security 3.0.5 and codex 3.0.5 exactly. Signed helpers changed in #4178 and were re-signed there. 
 Added 
 
 ruflo tui draws the console's pictures, looks and motion (console 0.44.x, #4182 , #4188 ): --look bbs|orbital|plain , --fps , --anim , --pictures , --boot , and any console view with --view . It draws at the default size when the terminal reports 0 columns ( #4160 , @martinvlad ). 
 
 Changed 
 
 ruflo init : the v3 implementation skills are opt-in ( --full adds them), like agents.v3 ( #4140 , #4139 , @z4forzubair ). 
 
 Fixed 
 
 MCP server and daemons : the server starts in the session project and ignores a CLAUDE_FLOW_CWD that names the home directory or a filesystem root ( cli-core 3.7.3); user-level claims resolve through os.homedir() on Windows; duplicate or zombie daemons per workspace are stopped ( #3987 , @socrates6969 ). Trajectory counts persist across processes and daemon jobs feed learning ( #3988 , @socrates6969 ). One node process per MCP session, with node:http and the security barrel kept off the startup path ( #3989 , @socrates6969 ). 
 Console reads the project on Windows (a drive path is absolute) ( #4177 , #4175 ). Neural data dir resolves through the project cwd; stored worker error text is capped. 
 Hooks and core : failed tool outcomes are recorded, hooks run from the project root, telemetry stays off the tool path ( #4178 ). 
 Memory : calibrated default search threshold with near-miss hints ( #4184 , #4129 ); memory_export reads the CLI store as well as AgentDB ( #4186 , #4148 ); the AgentDB directory is created before the bridge opens it ( #4155 , #4132 , @martinvlad ); TieredMemoryStore recalls multi-word and natural-language queries ( memory 3.0.5, #4183 , #4152 ). 
 Intelligence : long memories recalled for short route prompts ( #4172 , @rudycelekli ); SONA reinforces the nearest pattern for near-identical tasks ( #4185 , #4134 ); AIDefence learns missed threats and autopilot learning loads ( #4187 , #4147 , #4146 ). 
 Workflow and agents : invalid gates and unsupported steps fail closed ( #4164 ); agent health derives from observed execution outcomes ( #4167 ) ( @rudycelekli ). 
 Analyze : classification from diff content and commit subjects, safe Git revision ranges, encryption paths flagged security-sensitive, accurate reviewer-role docs ( #4165 , #4162 , #4169 , #4163 , @rudycelekli ). 
 Security scan : interpolated exec calls after imports are detected ( #4166 , @rudycelekli ); a failed npm audit reports "could not scan" instead of a clean tree ( #4154 , #4124 , @martinvlad ). 
 Clear "not installed" message for @ruvector/rvagent-wasm ; only new patterns are counted ( #4179 , #3979 ). Skills, plugin contracts and ruvector/neural/kg surfaces ( #4181 ). 
 
 Notes 
 
 @claude-flow/browser (agent-browser bump, #4130 ) is a standalone package outside this train and was not republished. 
 
 Thanks 
 @rudycelekli , @martinvlad , @proffesor-for-testing , @ronmikailov , @z4forzubair , @socrates6969 , @nicholas-ruest and @pacphi for the fixes and reports across 3.56.6 to 3.56.10.