---
id: inbox_cd41dbf6
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0102-lobsters-vibecoding-the-decoherence-trap-when-ai-slop-drowns-833e]]"
title: "The Decoherence Trap: When AI slop drowns out the signal in an endless sea of noise"
url: https://maevyn.codes/decoherence
source: lobsters-vibecoding
published_at: 2026-10-16T11:36:29-05:00
fetched_at: 2026-10-25T01:28:46.806936+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "系統裡堆滿各自成立、彼此卻不相容的模型，改動成本就被翻譯與副作用吞掉。 **Why** 作者認為 AI 大量生成程式碼正以不可持續的速度製造這種累積，而這種累積也會限制 AI 遞迴自我改進的速度。 **How** 作者以水管修補與 Ship of Theseus 為類比，說明逐段修補卻不統一模型，複雜度會隨組合爆炸，而壓力會讓工程師草率收尾。 **What** 文中以模擬呈現程式碼一致性與開發速度的關係，形成「甜蜜點」曲線；低於甜蜜點時，速度急劇下降。"
key_points:
  - "decoherence 定義為局部有效但彼此不相容或重複的模型累積，改動成本主要花在模型間的翻譯與避免副作用"
  - "作者以水管分段更換為例：新舊管混用後，每個接點都需要同時懂兩套系統的專家，加入第二次轉換前未完成第一次，複雜度會組合式增長"
  - "文中模擬依 coherence factor 繪製功能產出分布，呈現「甜蜜點」形狀，作者主張此模式是工程師熟悉的現象"
tags: [decoherence, tech-debt, code-complexity, ai-coding, recursive-self-improvement]
topics: [engineering.architecture, agents.coding_agents]
importance: 3
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Decoherence Trap: When AI slop drowns out the signal in an endless sea of noise

系統裡堆滿各自成立、彼此卻不相容的模型，改動成本就被翻譯與副作用吞掉。 **Why** 作者認為 AI 大量生成程式碼正以不可持續的速度製造這種累積，而這種累積也會限制 AI 遞迴自我改進的速度。 **How** 作者以水管修補與 Ship of Theseus 為類比，說明逐段修補卻不統一模型，複雜度會隨組合爆炸，而壓力會讓工程師草率收尾。 **What** 文中以模擬呈現程式碼一致性與開發速度的關係，形成「甜蜜點」曲線；低於甜蜜點時，速度急劇下降。

### 重點
- decoherence 定義為局部有效但彼此不相容或重複的模型累積，改動成本主要花在模型間的翻譯與避免副作用
- 作者以水管分段更換為例：新舊管混用後，每個接點都需要同時懂兩套系統的專家，加入第二次轉換前未完成第一次，複雜度會組合式增長
- 文中模擬依 coherence factor 繪製功能產出分布，呈現「甜蜜點」形狀，作者主張此模式是工程師熟悉的現象

**原文：** [lobsters-vibecoding](https://maevyn.codes/decoherence)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

TL;DR

Evolution

The Maze

Simulation

Progression

Singularity

Better Software

Mathematics

Collapse

Get notified

Get notified

Citations

This essay introduces the concept of decoherence : the accumulation of locally valid but mutually incompatible or redundant models within a system, such that the cost of change is dominated by translating among those models and preventing unintended side-effects.

←

←

→

→

In other words, it's what happens when slop drowns out the signal in an endless sea of noise.

Decoherence grows relative to the rate of change of a system, and it increases faster the more decoherent a system is, resulting in runaway exponential growth. It is not a new phenomenon, and humans have always countered it through carefully finding ways to do more with less, unifying disparate patterns and models into a cohesive whole. However, the widespread use of AI is currently producing it at a rate that is unsustainable.

The good news is that this rules out the specter of runaway recursive self-improvement, the intelligence explosion that goes parabolic before anyone can react, as decoherence both prevents AI from improving in a bubble and limits the rate at which it can improve outside of it. The bad news is that we are barreling toward a different kind of disaster: Decoherence Collapse.

Imagine a building, let's say a small office tower. When this building was built, they used a type of pipe that will degrade over time and eventually need to be replaced. This is standard infrastructural debt ; basic wear and tear, as they say.

Then, let's say that when it comes time to replace the pipes, you need to change them over to a new standard. This could be because of new building code requirements, because the old pipes simply aren't made anymore, or because the new pipes are much better and easier to maintain. This is standard technical advancement debt , the need to upgrade and transition due to the forward progress of technology over time.

There is a third form of debt that can arise based on how the transition from old pipes to new pipes is done. Consider the following options:

For most people, option 3 is very appealing. It allows them to keep things running smoothly and to spread out the cost of maintenance. And if we can just make like the Ship of Theseus [ 1 ] and replace the pipes one at a time, why shouldn't we?

Well, for one thing, it creates decoherence .

And decoherence is, by far, the worst form of tech debt.

The Ship of Theseus actually gives us a good lens for understanding the true scope of decoherence. We know how to build ships made of wood, and we know how to build ships made of steel. You can repair a ship one piece at a time with the same material, as the original thought experiment goes, and the ship remains functional, with all of the original designs and structures that went into it intact.

But do we know how to build every iteration of a ship in between wood and steel? Could you, say, slowly replace every piece of a man-of-war and incrementally turn it into a modern destroyer? And have it functional (for some definition of functional) at every step in the process?

It's not that the answer is an absolute "no". If we are creative enough, if we had the best minds working on it, then I'm sure there would be some path to doing this. But it would require ingenuity and skill and craftsmanship . It would require attention to detail. And, crucially, you would really want to complete the process, because the half-man-of-war, half-destroyer vessel is likely not going to be very good in modern combat.

Returning to our plumbing example, we can see how the same strategy plays out regularly in the world of construction. Every time a pipe breaks, the plumber is called, walls are opened, the repair is hand-crafted for that specific area, and then everything is closed back up. If you're lucky, the plumber will leave detailed notes, and if you're not, then years later some poor sod is going to open that wall back up and say to themselves, "What the hell is going on here?"

Now, multiply that process over time as we slowly replace the pipes in our building, and the end result is a patchwork of old and new pipe that has much more complexity than either system on its own. Every joint, every hand-crafted patch, is its own little bundle of unique forces and properties that are understudied, and thus requires an expert in both systems to fully understand and work with.

On the surface, this is fine. The pipes work, why does it matter how they work? As long as it's a good patch, who cares?

Well, what happens if we, say, want to build an annex?

For the purposes of this thought experiment, we'll say that the water for the annex needs to be routed through at least part of our existing building, using the existing pipes. And, crucially, we need to increase the overall water pressure in the system.

Now, the question is: Is it safe to increase the pressure?

If we had all type A or all type B pipes, even ones that had been patched and repaired over time, then this would be a straightforward question. Both systems are well understood, both have tools and processes for calculating their capacity, and people run these calculations all of the time.

But, if we have an unknown mixture of both systems, suddenly we have to do a lot more analysis to answer that question. Every patch could change the answer, even ones at the other end of the system, because they're all tied together.

And this is where the true complexity of decoherence becomes clear. When we try to make changes to decoherent systems, it requires far more expertise and skill than working with either system alone. The engineer working on the system needs to trace and understand it much more thoroughly and carefully, because their changes may have unintended consequences. ( And yes, I count plumbers as engineers, at least as much as software devs. Have you seen them think through pressure forces in drain pipes in real time? It's remarkable. )

That is no small task, and it is best if it's not rushed. But for the outside observer, without an understanding of the depth of the problem, this can be frustrating. Normally this part is easy. Why is it taking so long this time?

In this situation, management will oftentimes apply pressure to get things done faster. When pressure is applied, the expert doesn't do the full analysis faster; they just stop earlier and do something they're pretty sure will work. A sloppy join, an unusual part, maybe some extra safeguards, just in case.

Not completing the task thoroughly, however, creates a knock-on effect: this particular change has lower quality, and it makes the system more fragile and complex. This means the next change will take even more thought and care, and if the pressure on the engineer is the same, then they will do an even worse job.

That is a pretty messy situation as it stands, and you can already see a sort of exponential growth of complexity taking place here. But wait, it gets worse! Let's consider the next level of decoherence: Starting a second transition before finishing the first.

The tricky part about software, as compared to a physical building or other types of real-world systems, is that it's all sort of invisible.

Coders walk through the halls of codebases every day. We navigate the labyrinth successfully so often that we become familiar with every corner and every turn, and when our walks become longer, with more corridors and dead ends and trap doors, we feel it much more immediately and intuitively.

But this is difficult to relate to people who can't even see the maze, who don't walk it with you every day. And when it comes time to clean up some of your debt, to make the maze shorter and less winding, your proposals are hard to sell up the chain, even to those who used to walk mazes a long time ago. In the end, none of them know your maze. They don't know the trials you face each and every time you enter it.

By comparison, our plumber friend in the real world can show the building owner the absurdity of their pipes much more directly .

When we start to mix more than two systems together, with multiple patches over time in a haphazard way, the complexity of the maze explodes . It is now combinatorial: you need to think of A -> B, A -> C, B -> C, A -> B -> C, C -> B -> A, and so on.

We can of course insulate engineers from this somewhat. We can come up with best practices, we can use tools and frameworks to isolate part of the system from another part (for instance, by using a pressure-limiting valve in our pipes). Inevitably, though, it gets to a point where even the best engineers, the smartest people, can no longer safely navigate the maze.

They may be able to do it 80 or 90% of the time, but they will eventually take a wrong turn

forget to leave a trail of string and find themselves stuck

This is the Decoherence Trap. The maze grows onward and onward until it swallows you whole and leaves you lost in the dark. Until it becomes so massive that it would take lifetimes to navigate.

Well, lifetimes for humans anyway. But what about AI?

Humans get tired and reach physical limits, but autonomous agent swarms can keep going around the clock, collectively and tirelessly mapping the maze like the good little robots they are. If scale is the problem, then shouldn't we just be able to throw more compute at it and call it a day?

Well, that depends on the nature of the complexity we are facing. Does it:

If it's the former, then yes, as the size of the problem grows we can just keep adding more agents and more data centers and working the problem at about the same pace. But if it's the latter , then adding more capacity will only get us the ability to push a bit further before the size of the maze threatens to consume all of the compute on Earth (and in space, should SpaceX's plans [ 3 ] work out).

In my experience, it is the latter. When a plumber opens up a wall and sees a mess, it isn't clear what's going on. They may choose to use pipe A, they may choose to use pipe B, or they may choose to add a new type of pipe entirely in their confusion. The same is even more true for code.

We can see this play out in a simple simulation below. Here, we have a graph that represents a codebase (or some other complex system), where:

Loading precomputed timeline...

This is a recording of a few runs. If you want to play with the full simulation yourself, changing the settings and watching what happens, you can find it here .

An actor, representing a developer, implements a "feature" by walking some random subsection of the graph and then mutating it. The actor's base behavior is shaped by its coherence factor :

At first, the lower-coherence actor moves very quickly compared to the higher-coherence actor. However, as the graph changes, it impacts the walks as well. Each of the following slows down the actor's progress:

If we take the distribution of features built over time and coherence, we can plot the result and see a shape that should look familiar to any engineer: The Sweet Spot .

In the Sweet Spot , the system is relatively coherent and we actively invest in it to ensure it stays that way. There are a few dominant paradigms, but there's enough jitter that things can change and adapt over time, and we aren't overly perfectionist about everything.

Above the Sweet Spot , we work extremely hard to make sure every new node fits into the existing paradigms, and we remove complexity at every turn. This takes much more time and slows down feature work, but in the worst case it still produces a highly coherent system that can be iterated through relatively quickly.

Below the Sweet Spot , the drop-off is precipitous. We very quickly lose speed as the codebase becomes exponentially more complex. If the coherence factor is negative , and no care is given to maintaining coherence, then the time to ship a feature grows without any apparent bo

[... truncated for safety ...]

</details>