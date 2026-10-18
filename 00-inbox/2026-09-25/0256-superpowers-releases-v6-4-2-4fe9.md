---
id: inbox_7624d1c3
source: superpowers-releases
source_type: rss
url: "https://github.com/obra/superpowers/releases/tag/v6.4.2"
author: "obra"
published_at: 2026-09-25T18:08:09+00:00
fetched_at: 2026-10-18T02:56:56.726312+00:00
content_hash: "4fe9db8adcc19f41b3eca14053efecec51dcc045577bdc978dc313faac5e98bd"
lang: en
caption_quality: None
raw: true
topics: []
---

# v6.4.2

writing-plans produces leaner plans, faster. Plans now record the decisions an implementer needs (signatures, test assertions, the spec's values) instead of writing out the code. Some frontier models, including Opus 5.5, could get overzealous during plan writing and, with certain prompting, would sometimes try to implement the entire project while designing the plan. The new skill keeps planning focused on the plan. When we reproduced the original report, the scratch builds went away, and plans took a quarter of the time and about a third of the tokens. Thanks to Harper Reed for the report and session bundle. ( #2333 ) 
 Writing Plans 
 
 A plan records decisions. It's not a transcript of the code. "What a Step Contains" replaces the "No Placeholders" section. A test step names the test and its assertions. A code step gives the exact signature, the file, and the spec's values, and includes a body only for an algorithm those don't determine. A verification step gives the command and its passing output. A reference to another task goes through that task's Interfaces block. Placeholders are still called out as the opposite failure. ( #2333 ) 
 Self-review checks proportion. The plan compares its own length to the spec's. A plan several times longer than the spec is a transcript, and when code blocks dominate, bodies get replaced with signatures and test assertions. ( #2333 ) 
 The plan's reader is described as capable: an engineer who writes idiomatic code once they know the exact interface and test. This replaces "zero context, questionable taste." Steps are now sized as "one action with a checkable result" instead of "2-5 minutes." ( #2333 ) 
 Every plan written by the new skill executed 9/9 against planted-defect probes on Sonnet 5, the same result as full-code plans. ( #2333 ) 
 Removed plan-document-reviewer-prompt.md . Nothing referenced it. ( #2333 ) 
 
 Documentation 
 
 Removed CLAUDE.md . Claude Code now reads AGENTS.md directly, but only when no CLAUDE.md exists, so keeping the one-line pointer would have hidden the real guidelines.