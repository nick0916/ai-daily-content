---
id: inbox_e20c4a2b
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/0020-lobsters-ai-building-fine-grained-version-control-fo-5620]]"
title: "Building fine-grained version control for agents with Rust and Durable Objects"
url: https://delta.dev/blog/fine-grained-version-control-for-agents
source: lobsters-ai
published_at: 2026-10-30T11:50:44-05:00
fetched_at: 2026-11-01T00:27:17.560084+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓每段程式碼都能追溯到產生它的對話與推理過程。 **Why** 寫程式的推理常留在 agent 對話中，或被壓縮進無人閱讀的 commit message 而遺失。 **How** DeltaDB 以 CRDT 組成的有向無環圖（DAG）存在本機 SQLite，每個 delta 是最小變更單位，快照以 copy-on-write B+ tree 快取，每個 thread 對應一個 Cloudflare Durable Object 同步。 **What** Zed Industries 發布 DeltaDB 與其第一方 agent harness Delta；文中以 timelines 讓子代理平行修改再合併，並說明版本向量在 actor 頻繁進出時只增不減，因此改用 DAG 祖先查詢。"
key_points:
  - "版本向量在人與 agent 頻繁進出時只會增長，故 DAG 的祖先查詢較合適"
  - "B+ tree 採原地修改，作者稱相較 SumTree 的前綴切割重建更快"
  - "每個 thread 對應一個 Durable Object，各 thread 之間 share-nothing，可隨 thread 數水平擴展"
tags: [crdt, version-control, agent-context, sqlite, durable-objects, zed]
topics: [agents.coding_agents, engineering.architecture]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Building fine-grained version control for agents with Rust and Durable Objects

讓每段程式碼都能追溯到產生它的對話與推理過程。

**Why** 寫程式的推理常留在 agent 對話中，或被壓縮進無人閱讀的 commit message 而遺失。

**How** DeltaDB 以 CRDT 組成的有向無環圖（DAG）存在本機 SQLite，每個 delta 是最小變更單位，快照以 copy-on-write B+ tree 快取，每個 thread 對應一個 Cloudflare Durable Object 同步。

**What** Zed Industries 發布 DeltaDB 與其第一方 agent harness Delta；文中以 timelines 讓子代理平行修改再合併，並說明版本向量在 actor 頻繁進出時只增不減，因此改用 DAG 祖先查詢。

### 重點
- 版本向量在人與 agent 頻繁進出時只會增長，故 DAG 的祖先查詢較合適
- B+ tree 採原地修改，作者稱相較 SumTree 的前綴切割重建更快
- 每個 thread 對應一個 Durable Object，各 thread 之間 share-nothing，可隨 thread 數水平擴展

**原文：** [lobsters-ai](https://delta.dev/blog/fine-grained-version-control-for-agents)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Architecture

The mighty B+ tree

Timelines and synchronization

One Durable Object per thread

#[derive(Replicate)]

Putting it all together in Delta’s native UI

Conclusion

Back in 2021, Nathan, Max and I founded Zed Industries with two goals: build a very fast code editor , and fundamentally change how teams collaborate on software . Millions of people now use Zed, and I’m proud of what we built .

For the past year, we’ve been working on the second goal.

I believe that writing software is the process of continuously clarifying a problem, in your head or with your teammates, until the code becomes inevitable. Clear thinking leads to clear code; messy thinking leads to messy code. Agents haven’t changed that. We’re just producing code way faster, and more and more of the clarifying happens in conversations with agents. In the best case, the context behind that code is trapped inside the agent harness of the week. In the worst case, it’s lost forever in Slack or compressed into a commit message that the agent wrote and that you didn’t read.

DeltaDB is our answer. It’s a version control system for agent context. You can point at a piece of code, recover the reasoning behind it, and ask the agent or human who wrote it why it looks the way it does.

In this post, we’ll dive into how we built a system that streams every change from humans and agents in real time, merges their edits into one monotonically growing causal graph, and keeps every edit linked to the conversation that produced it.

As always at Zed Industries, we started with an empty repo.

DeltaDB is a collection of CRDTs , all stored locally in SQLite and linked together in a directed acyclic graph (DAG). Every node in the graph is called a delta , and it’s the smallest unit of change that can be represented. Combined, this lets us model the essential state of an agent thread : its conversation, its files, and everything around them.

Using CRDTs lets clients make progress on their own and stay resilient to network failures or partitions. We eventually synchronize all the state to a server, but we don’t need clients to be constantly connected: changes are applied locally right away and synchronized when possible. This makes it straightforward to implement the entire spectrum of collaboration, from handing off a thread asynchronously to collaborating in real time with your teammates .

The DAG enables representing every possible intermediate state in the system. This has a few nice properties. For example, we can easily scrub back and forth through the history of a thread and its worktree. It also lets us express the entire state of the system with a very compact version: the deltas at the tips of the graph (also called a frontier ). Its size grows with how many branches are open at the same time, not with how many writers there have ever been. Our design closely resembles the work pioneered by Gentle and Kleppmann in the Eg-walker paper .

The primary downside of using a DAG is that we need to navigate the graph to detect whether a delta already includes the impact of some other delta. If we used a version vector , we could answer that by comparing counters. Even though that would be cheaper than walking the parent links, a version vector assumes that actors are few and long-lived. In a thread, however, people and agents come and go all the time, and once an actor makes some changes, the vector can’t drop the counter. So the vector can only ever grow, even after the actor has left. Dotted version vectors have similar issues, as illustrated in the animation below.

Ancestor queries are a fine tradeoff for us because we need to store every version anyway. They’re also fast in practice, because we store a delta’s ancestry separately from its payload. The ancestry data is tiny and stored in causal order, so these queries can leverage a lot of locality.

Making each delta a node in the DAG also lets us decouple its network representation from how the CRDT expresses its impact internally. For example, this is how we define text edits:

Note how parent and offset are sufficient to uniquely identify a position in a buffer, even in the presence of concurrent edits. Most of the time, the buffer is already at parent , so the edit applies directly. When it isn’t (e.g., if a concurrent edit happened in the meantime), the client reifies the version at parent , reconstructing the buffer as it was at that point. It then translates the offset into an internal representation (fragment IDs in our case, similar to how we do it in Zed) and locates that fragment ID in the buffer at the version we’re applying the edit to.

This makes deltas very cheap on the wire and it also lets us change the internal fragment representation and page out unused fragments.

We store all of our data in SQLite. This data can roughly be partitioned into two categories: relational and versioned.

Relational data is pretty straightforward. For example, on the client we store all the threads that you’ve created or opened. This goes in a traditional table and there’s nothing special about it.

Versioned data is where it gets interesting. The whole system hinges on the ability to quickly reify any version. As we saw above, applying a concurrent delta depends on it, and we also don’t want to wait a long time when scrubbing through history or mounting the worktree of an old version of the thread on the file system.

To make that fast, we cache a snapshot of the whole state for recently used nodes in the DAG (plus a few more important versions that we pin). Then, starting from the version we want, we walk back through the DAG to the closest ancestor that has a cached snapshot and apply every delta in between.

Storing a full copy of the CRDTs for every cached version would be prohibitively expensive. Instead, we express the whole state as copy-on-write B+ trees. This means we can reuse most of the nodes from a previous snapshot and only pay for the paths that the replayed deltas touch.

Our B+ tree is a variation of Zed’s SumTree . The SumTree in Zed is an append-only B+ tree whose internal nodes summarize their children. To edit a SumTree , you have to slice a prefix of the tree up until the insertion point, push new items and skip the ones you want to delete, and finally append the suffix, which rebuilds every node along the cut. In contrast, DeltaDB’s B+ tree edits in place through a mutable cursor.

It’s a lot faster because we perform way fewer adjustments to the tree (see the animation below). In-place mutation also lets us precisely track which nodes were allocated, changed, or released. On commit, new nodes become inserts, changed nodes get rewritten in their existing row, and released nodes only get their refcount decremented. All nodes get stored in a generic nodes table.

Clients can track as many frontiers as they want in the DAG using timelines . For example, when kicking off a subagent, we create a new timeline parked at the parent thread’s frontier and start making changes in parallel. All timelines share the same DAG so they can be merged back together at any later point in time. None of this touches Git and, crucially, doesn’t require committing for cross-agent coordination.

Timelines are also used for synchronization among clients. When a thread is shared, the client establishes a WebSocket connection to the server and subscribes to the timelines it is interested in. For every timeline, we perform a synchronization step to exchange all the deltas each side has missed since the last connection (or everything if it’s the first time we’re connecting to the server). This is accomplished by walking the DAG and sending a logarithmically spaced list of versions to find a recent common ancestor. Every new delta is then sent incrementally over the WebSocket, saved by the server, and pushed to every other client subscribed to that timeline.

Reconnections are handled the same way, which makes it straightforward to reason about the correctness of delta delivery.

We envision a world where every human creates and interacts with more and more agents. In that future, it’s hard to imagine keeping all the thread state in a single server.

In DeltaDB, every thread gets synchronized to its own Cloudflare Durable Object . The object comes to life the first time a client connects to it, and creating a thread costs nothing on the server. Each client establishes one WebSocket connection for every thread it’s interested in.

Other than authentication (which only happens when establishing the connection), this is essentially a share-nothing architecture. This means we scale horizontally with the number of threads, as far as Cloudflare can serve the traffic.

This lets us scale across threads, but multiple agents and humans can also issue many simultaneous writes within a single thread. We put a lot of work into making that efficient and cost-effective in a Durable Object, and we will discuss how we did it in a future post.

Cloudflare is DeltaDB’s first deployment target. As of today, it runs on our multi-tenant deployment, as well as on single-tenant deployments for customers who want to “bring their own Cloudflare”. However, the whole system has been designed to be portable to other platforms, so long as they provide an object store, a fault-tolerant Postgres database for authentication, and a way to spin up addressable single-threaded processes with their own transactional storage.

In practice, we never need to think about any of the above when interacting with DeltaDB. The whole system is exposed via a higher-level client API with the following primitives:

We have a long-lived deltadb::Client struct that can be used to interact with the above primitives:

Updating a primitive automatically mints new deltas and adds them to the DAG, which is then synchronized to disk and to the server on the user’s behalf. You can also compose them into more complex structs using the #[derive(Replicate)] macro, and that’s indeed what we do to represent an agent thread.

If we peek under the hood, these types are just pointers into a larger, flat CRDT that we call a Snapshot . These pointers can be created at compile-time via the field attribute, or at runtime by taking the ID of the delta that created it.

The client API doesn’t expose the flat snapshot directly, but it exposes its data through the pointer mechanism described above.

You can use DeltaDB today via the CLI or using plugins that integrate with third-party agentic harnesses. The CLI already runs in its own process, so interacting with SQLite directly is totally fine there.

But our company’s history is one of vertical integration and fixing problems end-to-end. Controlling the whole stack lets us design the UX we want rather than working around someone else’s idea of how you’re supposed to interact with an agent. That’s why we built Delta , our first-party agentic harness. I believe it’s the state of the art for agentic coding, and it shares many of the underpinnings that make Zed as fast as it is.

In a native UI, the situation is very different: you need to render at the display’s refresh rate, so performing expensive operations on the main thread (such as blocking I/O) would blow right past our tight 8 ms frame budget.

The good news is that the API showcased above is actually designed to be interacted with from the main thread. We achieved this by maintaining an Arc -allocated version of the Snapshot that gets created during the initial load, which is a moment where we can afford an asynchronous pause to load from the database. From then on, the main thread mints deltas synchronously as it manipulates the replicated primitives. Those deltas are then shipped asynchronously to a background thread alongside a clone of the snapshot. Remember that cloning a snapshot is cheap because we only use copy-on-write data structures.

In the background, we keep one dedicated writer thread and between two and four reader 

[... truncated for safety ...]

</details>