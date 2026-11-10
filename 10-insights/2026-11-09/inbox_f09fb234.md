---
id: inbox_f09fb234
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2341-simon-willison-the-web-is-more-than-enough-by-paul-ford-87d9]]"
title: "The Web Is More Than Enough, by Paul Ford"
url: https://simonwillison.net/2026/Nov/9/hn-50421091/
source: simon-willison
published_at: 2026-11-09T04:32:33+00:00
fetched_at: 2026-11-10T00:02:34.870688+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 實測 Claude 能把 Three.js 的 3D 作品改寫成不依賴函式庫的純 JS + WebGL。 **Why** Paul Ford 的文章主張網頁本身就足夠，Simon 受 HN 留言說服而動手嘗試。 **How** 他先在 Claude Chat 用 Three.js 做出一個海蛞蝓主題的法貝熱彩蛋，再於同一對話請 Claude 移植成 Vanilla JS。 **What** Three.js 版 77KB、Vanilla JS 版 98KB，兩者輸出不完全相同（Simon 不確定原因）；他認為 Claude Opus 5.5 Medium 能勝任純 WebGL 的 3D 建模，但自己覺得 Three.js 程式碼較易讀。"
key_points:
  - "Claude Opus 5.5 Medium 在 Claude Chat 中把 Three.js 的 3D 彩蛋移植成 Vanilla JS + WebGL"
  - "檔案大小：Three.js 版 77KB、Vanilla JS 版 98KB，兩版呈現不完全相同"
  - "Simon 覺得 Three.js 程式碼較易讀，但因為很少讀這類 3D 專案的程式碼，影響不大"
tags: [simon-willison, claude-opus-5-5, webgl, threejs, vanilla-js]
topics: [foundation_models.claude, agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## The Web Is More Than Enough, by Paul Ford

Simon Willison 實測 Claude 能把 Three.js 的 3D 作品改寫成不依賴函式庫的純 JS + WebGL。

**Why** Paul Ford 的文章主張網頁本身就足夠，Simon 受 HN 留言說服而動手嘗試。

**How** 他先在 Claude Chat 用 Three.js 做出一個海蛞蝓主題的法貝熱彩蛋，再於同一對話請 Claude 移植成 Vanilla JS。

**What** Three.js 版 77KB、Vanilla JS 版 98KB，兩者輸出不完全相同（Simon 不確定原因）；他認為 Claude Opus 5.5 Medium 能勝任純 WebGL 的 3D 建模，但自己覺得 Three.js 程式碼較易讀。

### 重點
- Claude Opus 5.5 Medium 在 Claude Chat 中把 Three.js 的 3D 彩蛋移植成 Vanilla JS + WebGL
- 檔案大小：Three.js 版 77KB、Vanilla JS 版 98KB，兩版呈現不完全相同
- Simon 覺得 Three.js 程式碼較易讀，但因為很少讀這類 3D 專案的程式碼，影響不大

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/9/hn-50421091/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

My comment on The Web Is More Than Enough, by Paul Ford — Hacker News. OK, this comment convinced me to give that a shot. 
 Here's a thing I made in Three.js this morning - a Nudibranch themed Faberge Egg: https://static.simonwillison.net/static/2026/Hidden-Reef-Egg... (77KB) 
 I just asked Claude (Opus 5.5 Medium running in regular Claude Chat) to port that to Vanilla JS, in the same thread where it had built it, and got this: https://static.simonwillison.net/static/2026/Hidden-Reef-Egg... (98KB) 
 They aren't identical - you can see what Claude said about that in the transcript (I don't fully understand why it differed): https://claude.ai/share/e56d163e-2793-4677-aa11-191d5058b414 
 But yeah, it turns out Claude Opus 5.5 is perfectly capable of 3D modeling in Vanilla JS + WebGL without Three.js. 
 In eyeballing the code I find the Three.js slightly easier to understand myself, but I rarely look at the code for these 3D projects so that isn't a particularly big deal. 
 
 
 Tags: hacker-news , javascript , ai , generative-ai , llms , claude , three-js

</details>