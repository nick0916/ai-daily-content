---
id: inbox_634d05bf
date: 2026-10-20
source_ref: "[[00-inbox/.../inbox_634d05bf]]"
title: "Battle Drones - a vibe coded RTS with audio-based multiplayer"
url: https://simonwillison.net/2026/Oct/20/battledrones/
source: simon-willison
published_at: 2026-10-20T19:34:19+00:00
fetched_at: 2026-10-21T00:15:27.181661+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 Claude Code 反覆迭代，做出一款能在手機玩的即時戰略遊戲，還能用聲音同步兩台裝置。 **Why** 作者原本認為 coding agent 只能做出看起來像遊戲、但不好玩的東西，想給模型一次機會證明他錯。 **How** 以 Claude Code for Web 的 Ultracode 模式（用 JavaScript 腳本協調多個 subagent 的 dynamic workflow）執行「Make it a LOT more fun」，過程中跑上千場模擬試玩，依結果重新平衡單位並加入新功能。 **What** Battle Drones 歷經 12 次大版本、321 個 commit（主要由 Claude Code 完成），支援手機與桌機瀏覽器、多張地圖與隨機地圖產生器、AI 個性、Agent vs Agent 模式，以及兩台相鄰裝置透過音訊同步的多人模式。v4「fun update」的 1,200 場 AI 對戰測試中，25 分鐘仍未分勝負的比例從 14% 降到 0.9%，落後 800+ scrap 的一方最終獲勝比例從 24% 升到 46%。作者幾乎沒審查程式碼（TypeScript），v8 起改為先請 Claude 研究並批判設計、同意後才動工。"
key_points:
  - "Ultracode 模式 + 一句「Make it a LOT more fun」：跑數小時、上千場模擬試玩後自行重新平衡，1,200 場 AI 對戰中 25 分鐘未分勝負比例 14% → 0.9%，落後方逆轉勝比例 24% → 46%"
  - "有明確設計意圖時，先要求 Claude 研究並批判設計、雙方同意修改後才動工（v8 Archipelago 地圖：島上 uplink 只能用 Condor 空運步兵佔領）"
  - "全專案 12 次迭代、321 個 commit，3D 模型全由 Claude 以 TypeScript 程式碼產生；作者幾乎未審查程式碼，主要靠實際試玩把關"
tags: [vibe-coding, claude-code, ultracode, game-dev, simulated-playtesting]
topics: [agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Battle Drones - a vibe coded RTS with audio-based multiplayer

用 Claude Code 反覆迭代，做出一款能在手機玩的即時戰略遊戲，還能用聲音同步兩台裝置。

**Why** 作者原本認為 coding agent 只能做出看起來像遊戲、但不好玩的東西，想給模型一次機會證明他錯。

**How** 以 Claude Code for Web 的 Ultracode 模式（用 JavaScript 腳本協調多個 subagent 的 dynamic workflow）執行「Make it a LOT more fun」，過程中跑上千場模擬試玩，依結果重新平衡單位並加入新功能。

**What** Battle Drones 歷經 12 次大版本、321 個 commit（主要由 Claude Code 完成），支援手機與桌機瀏覽器、多張地圖與隨機地圖產生器、AI 個性、Agent vs Agent 模式，以及兩台相鄰裝置透過音訊同步的多人模式。v4「fun update」的 1,200 場 AI 對戰測試中，25 分鐘仍未分勝負的比例從 14% 降到 0.9%，落後 800+ scrap 的一方最終獲勝比例從 24% 升到 46%。作者幾乎沒審查程式碼（TypeScript），v8 起改為先請 Claude 研究並批判設計、同意後才動工。

### 重點
- Ultracode 模式 + 一句「Make it a LOT more fun」：跑數小時、上千場模擬試玩後自行重新平衡，1,200 場 AI 對戰中 25 分鐘未分勝負比例 14% → 0.9%，落後方逆轉勝比例 24% → 46%
- 有明確設計意圖時，先要求 Claude 研究並批判設計、雙方同意修改後才動工（v8 Archipelago 地圖：島上 uplink 只能用 Condor 空運步兵佔領）
- 全專案 12 次迭代、321 個 commit，3D 模型全由 Claude 以 TypeScript 程式碼產生；作者幾乎未審查程式碼，主要靠實際試玩把關

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/20/battledrones/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Battle Drones - a vibe coded RTS with audio-based multiplayer

My latest vibe coded game experiment is a Command &amp; Conquer style RTS (Real Time Strategy) game called Battle Drones ( play it here ). Unlike my previous experiments , this one is actually fun to play . I'm somewhat embarrassed to admit that I got there by telling Claude to "Make it a LOT more fun". It also supports multiplayer between nearby devices using audio to synchronize game state! Here's what I've built so far, and some of the things I learned along the way. 

 
 Battle Drones 
 How I built this 
 v1: the initial prototype 
 v2: full sprites 
 v3: varied terrain 
 v4: the fun update 
 v5: Battle Drones goes 3D 
 v8: Archipelago 
 v10: Goliath, and agent battles 
 Agent battles 
 v11: Random Maps 
 v12: Multiplayer via sound 
 Some thoughts 
 Update: Online multiplayer support 
 

 Battle Drones 
 My initial goal was to build an RTS game I could play on my phone, in the style of Command &amp; Conquer . I have fond memories of the 1995 original (I liked Red Alert too) and wanted to recapture a little bit of the magic. 
 After 12 major iterations (and 321 commits by coding agents, mainly Claude Code) I now have a browser-based game that works on mobile and desktop, has multiple play modes, several maps (including a random map generator) and even supports multiplayer for two devices within microphone range of each other. 
 Here's a video demo of Battle Drones running in a desktop browser: 

 

 Features so far include: 
 
 9 buildings, 7 ground vehicles, 6 aerial vehicles, 3 infantry units - all 3D models, which you can browse here 
 
 Fog of war 
 Different weapons are needed to target aerial or ground vehicles 
 
 Six maps , across five biomes - temperate, desert, arctic, volcanic, tropical 
 A random map generator 
 
 Skirmish mode - red vs. blue on a rotationally symmetrical map 
 
 Last Stand mode - one player holds out against as many waves of enemies as possible 
 Area effect weapons: Barrage, EMP, Drop Pod, Sky Hammer 
 
 Crate drops with bonus resources 
 In-game music that responds to events - it gets more intense as fighting breaks out 
 Different in-game AI personalities (Balanced, Rush, Air Swarm, Boom, Skyforce, Ironclad) 
 
 AI vs. AI mode, to watch those personalities play each other 
 The Goliath - a giant stomping mech with laser eyes and arm cannons and the ability to establish a new base 
 
 Mutators that add extra rules or twists 
 A "Daily Op" challenge 
 Ranks and achievements ( Medals ) 
 
 Agent vs. Agent mode where two LLMs can play Battle Drones against each other 
 A multiplayer mode based on two nearby phones communicating via audio messages, an extension of my earlier experiment with Chirp Pong 
 
 
 How I built this 
 Battle Drones is heavily vibe coded - I've reviewed almost none of the code, and it's built in a language (TypeScript) that I've hardly used myself. I've playtested it quite a bit though, and it's been through a large number of iterations since I started the project. 
 Here's a rough history of the project so far, including key prompts and links to transcripts. 
 v1: the initial prototype 
 I started out with Claude Fable 5 back in July: 
 
 We are going to build a mobile friendly RTS game - command and conquer style - called Battle Drones, in which two armies of drones (both flying and ground-based) battle for territory and resources 
 Let's start with a MVP design, ask me some questions 
 
 Here's a shared transcript . I'd given Claude Code for Web an environment variable with an OpenAI API key and told it to use the OpenAI Image Generation API for assets, which got me some basic sprites. 
 You can try v1 here - it looked like this: 
 
 It's recognizable as an RTS, has building mechanics and the ability to select and direct units, and a basic AI to play against. 

 This first version was barely a proof of concept, and it wasn't any fun to play. 
 Claude used the Phaser 2D game framework for these early versions. I didn't even realize this until several iterations later! 
 v2: full sprites 
 The second version ( try v2 here ) added sprites for all of the vehicles and the "AI vs. AI" mode, so I could watch the game playing without having to directly control it myself. 
 Claude proved reasonably competent at prompting OpenAI's image models to generate sprites. You can browse the v2 sprites in the public/assets/sprites folder. 
 
 v3: varied terrain 
 It still wasn't much fun, and the graphics were boring. It was now October, and I had upgraded to Claude Opus 5.5. I told it: 
 
 Massively improve this game. Make the graphics and gameplay better (keep it mobile friendly). Render new graphics using the latest OpenAI GPT image API (lookup details) with the API key in the environment variable. Add new unit types and balance the gameplay better. Also add new buildings and better, more varied terrain. 
 
 This resulted in five new maps with generated background tiles in a variety of styles, visible here . Opus also regenerated the sprites, making them much more visually appealing. You can try v3 here - it looks like this: 
 
 This is starting to feel like a real game! It still wasn't very fun to play though - I found myself getting bored pretty quickly. 
 v4: the fun update 
 So far my Battle Drones experiment was confirming my previous belief that coding agents can build a thing that looks like a game but can't actually make something that's genuinely compelling to play. 
 I shared this theory with someone over dinner, and then thought to myself that I should give the models a proper chance to prove me wrong. I prompted Opus 5.5 on my phone: 
 
 This game isn't fun enough yet. Make it a LOT more fun. 
 
 This time I was running in Ultracode mode , where Claude Code (in this case Claude Code for Web) runs "dynamic workflows", described in their docs as: 
 
 A dynamic workflow is a JavaScript script that orchestrates many subagents at once. 
 
 This kicked off many hours of work. I started it in the evening and didn't get a playable result back until late into the next morning. But the results were spectacular. 
 You can try v4 here - it looks like this: 
 
 I had Claude write its own release notes - here are the highlights: 
 
 Every skirmish and Daily Op now opens with a choice, gives the side that's losing a way back, and pulls the armies into the middle of the map. There are also two new ways to play. 
 
 
 Openers : pick Blitz, Industry or Air Wing before the clock starts. 
 
 Call-down powers : Barrage, EMP, Drop Pod and the Sky Hammer orbital strike. 
 
 Objectives and salvage : Uplink relays, supply drops and wrecks worth scrap. 
 
 Feel : combat juice, adaptive music, unit voices and an announcer. 
 
 Command : battle alerts, game speed, saved squads and touch placement. 
 
 New modes : Last Stand survival waves and an 8-mission Ops campaign. 
 
 Progression : heroes, an after-action report with awards, a career, 7 mutators and a Daily Op. 
 
 Fights run longer and swing more. In 1,200 AI-vs-AI test matches on Normal, games still undecided after 25 minutes fell from 14% to 0.9%. The share of wins by a side that had been 800+ scrap behind rose from 24% to 46%. 
 
 Part of the reason Claude took so long was that it ran over a thousand simulated playtest sessions, and used the results to rebalance the existing units, add new ones, and introduce new features. 
 v5: Battle Drones goes 3D 
 After the success of Ultracode at "Make it a LOT more fun", I decided to be more ambitious: 
 
 Port this game to three.js with 3D models for all of the buildings and vehicles and landscapes 
 
 That was another overnight run. I woke up to this v5 version : 
 
 The new 3D models were entirely constructed by Claude in TypeScript code. 
 v6 ( play v6 here ) added some more visual polish. v7 ( play v7 ) added robot infantry (troopers, rocket squads, snipers) and a "Condor" troop carrying aircraft. 
 v8: Archipelago 
 I was beginning to feel guilty at how little actual design input I had into the game - it really had been a case of me saying "make it more fun" and "add visual polish" for the past few releases. 
 I'd noticed that the AI didn't use the new infantry and troop carrying aircraft from v7 very often - there wasn't a great strategic reason to use them. 
 It would be neat if we had a new map with a new game mechanic that actively encouraged players to load up Condors with infantry robots and send them out into the map. 
 This resulted in my longest prompt yet: 
 
 Design a new map. Goal is to make different strategic incentives that encourage use of Infantry and Condors and aerial vehicles. 
 To do this the map will have limited harvester resources but several more uplinks - but uplinks will be on islands that are inaccessible by land vehicles or infantry. These uplinks can also not be claimed using air vehicles. The ONLY way to get them is to fly infantry there in a Condor. 
 Armies always start with a Condor and a single squad. If an army has no Condor a new one will be provided for free, flying in from the edge closest to their HQ and landing there. That free condor will come with a single free squad on board. 
 The two HQs should be entirely separated by water, but still accessible by vehicles thanks to two bridges across the map in different places 
 I want to encourage a battle over uplinks. 
 The map should be the times the size of other maps - still square 
 First research and then critique this design. Only build after we have agreed on any modifications 
 You get to design a new biome for this 
 
 The result was the tropical Archipelago map, with seven island uplinks that players can only capture by flying out infantry in a Condor. It's definitely the most fun map to play, once you've got the hang of the basic game mechanics from the simpler maps. The v9 edition made that map a little more interesting - it now looks like this: 
 
 v10: Goliath, and agent battles 
 I decided to add giant robot mechs to the game - think Jaegers from Pacific Rim , or Titans from Warhammer 40,000. 
 Here are some of the prompts I used to brainstorm with Claude: 
 
 Help me brainstorm ideas for adding giant robots to this game - think dreadnoughts or titans from W20K - how could we do this in a way that enhanced gameplay, kept things balanced, added unique twist? Don't overthink this yet 
 
 
 Let's keep brainstorming. I like the idea that it's a mobile base - that can accept harvested scrap and can have buildings built near it (even if it later moves on) and can produce infantry units too. An interaction with condor would be neat but I don't know what that could be. 
 
 
 Idea: as it gets damage it loses the ability to fire some weapons - by default it has eye laser (like lancers) and arm canons (like titan) and two shoulder mounted mortars, plus machine guns similar to a squad of troops 
 
 
 Damage knocks out mortars and then laser - it always has guns. You can't build next to a building that was only put there because of the mech, you need the mech there for off-base building and only within three squares of it 
 
 
 [...] Lets do two condors can carry the mech 
 
 The end result is really cool . 

 
 
 Your browser does not support HTML video.
 

 Goliaths can be constructed using a Gantry - a building that can only be created after first building a Fab, Bay, Airpad, and Tech Lab. You can see the Goliath under construction, and it then walks out from the Gantry and can march around the map. 
 Goliaths can "anchor", which digs them into the ground. In their anchored state they can act as a new HQ, constructing infantry units and additional buildings in a new area. 
 Two Condor aircraft can hook onto a Goliath, at which point it can be flown around the map! 
 The game now ends when you destroy the enemy's HQ building and any Goliaths they might have built. 
 There are also a couple of mutators relating to Goliaths: 
 
 
 Goliath Armada starts each side with four airborne Goliath

[... truncated for safety ...]

</details>