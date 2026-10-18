---
id: inbox_ce1daea1
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.57.0"
author: "ruvnet"
published_at: 2026-10-17T22:38:55+00:00
fetched_at: 2026-10-18T02:56:54.633868+00:00
content_hash: "7462ae2ac08611933204cb91693108daf5775ce0d58d7fe36922359a2e4367de"
lang: en
caption_quality: None
raw: true
topics: []
---

# v3.57.0 — community PR batch + policy-ledger integrity fix

Minor release: @claude-flow/cli , claude-flow , ruflo 3.57.0. A batch of community and dream-cycle fixes ( #4210 - #4252 ) plus a policy-ledger integrity fix ( #3892 ). No standalone leaf republish needed this round. 
 Security 
 
 ruflo init / init --dual / @claude-flow/codex init no longer write a permissive .codex/config.toml by default. The generated file now uses sandbox_mode = "workspace-write" , approval_policy = "on-request" and web_search = "cached" ( standard trust); the old danger-full-access / never / live file needs an explicit --codex-trust full (or RUFLO_CODEX_TRUST=full ). init prints which level was written, an existing .codex/config.toml is never rewritten (not even with --force ), and a kept permissive file is flagged with how to tighten it. Found by the three-host e2e run (ADR-490). @claude-flow/codex 3.0.4 (bundled, ships with the next train). 
 The MCP bridge on loopback no longer accepts tool-call requests from an arbitrary web page: local-only mode now requires the Host to be loopback (blocks DNS rebinding) and the Origin to be loopback-or-allowlisted when no MCP_AUTH_TOKEN is set ( #4226 , #4243 , @kevin9327 ). 
 The policy ledger now authenticates a retained/pruned ledger against its independent on-disk archive anchor instead of trusting the mutable state.json alone, and streams full audits through fenced writers. Fixes policy-ledger-verification-failed on any install whose ledger has already been pruned ( #3892 , #4216 , @proffesor-for-testing ). 
 
 Added 
 
 ruflo doctor reports better-sqlite3 copies compiled against Node 24.19+ headers when running Node 24.19–24.21, where they can abort the process ( Assertion failed: (env) != nullptr , nodejs/node#65446 ), with the documented workarounds. doctor --component native-addon runs it alone ( #4055 , reported by @ronmikailov ). 
 ruflo doctor reports health checks as versioned JSON output ( #4228 , @bryanbans ). 
 
 Fixed 
 
 @metaharness/darwin pin bumped from ~0.10.2 to ~0.12.0 , unblocking the metaharness-pin-drift CI gate repo-wide ( #3219 , #4252 ). 
 Swarm: subscriber delivery is cancelled cleanly at shutdown, acknowledgements are tracked per recipient, urgent messages survive queue overflow, and failed/cancelled task workers release their slot ( #4233 , #4234 , #4235 , #4236 , @rudycelekli ). Coordinator cancellation stays terminal ( #4244 , @rudycelekli ); domain pools stop creating unregistered agents and release agents after terminal tasks ( #4246 , #4247 , @Tong-bit-art ); shared worker reservations are honored across agent pools, fixing a case where that bookkeeping change would have silently defeated the domain-pool-release fix above ( #4245 , @rudycelekli ). 
 Learning stats read-merge-write transactions are serialized across processes, fixing lost concurrent increments ( #4217 , #4240 , @rudycelekli ). 
 Claude memories refresh across project and worktree roots ( #4210 , @rudycelekli ); the secret screen no longer treats a hyphen-named memory key as a credential field ( #4202 , #4211 , @akushonkamen ). 
 Hook lifecycle events are distinguished during deduplication, fixing the Stop hook claiming the session-end de-dup key so later hooks never ran ( #4206 , #4212 , @dajiaohuang ); init omits unimplemented generated hooks ( #4200 , #4213 , @dajiaohuang ) and stops granting blanket execution of project helpers ( #4221 , @xiajiahang ). 
 Intelligence: trajectories are forwarded using the ruvllm contract ( #4222 , @xiajiahang ); neural quantization reports unchanged persisted storage instead of a false delta ( #4224 , @dajiaohuang ). 
 Console: Mission Control's prose wraps at 80 columns ( #3899 , #4225 , console 0.44.3, @korjavin ); the mission ledger is keyed per project instead of leaking one project's active mission into every other ( #4237 , #4242 , @kevin9327 ). 
 daemon status reports the running daemon's actual TTL instead of a stale --ttl 0 default ( #4238 , #4241 , @kevin9327 ). 
 CLI: --no-color is honored for help and version output, and --no-update is honored before the startup update check runs ( #4248 , #4251 , @shuaiyafei ). 
 dream(performance) : RaftConsensus.awaitConsensus() is event-driven instead of busy-polling ( #4214 , #4215 ). 
 Docs: 25 user guide links repaired to v3 packages ( #4223 , @ketpatil77 ); ABP-governed SGit memory checkpoints and Ruflo CLI recovery validation documented ( #4239 , @mondweep ). 
 
 Not included: #4220 (helper-execution-permission fix) touches a signed helper manifest and needs a re-sign with the private key before merge, held for a follow-up release. #4216 's own large diff (ledger integrity) was reviewed in depth separately before merging, given it gates MCP tool-call authorization.