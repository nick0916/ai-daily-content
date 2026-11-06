---
id: inbox_187fdcd8
date: 2026-11-06
source_ref: "[[00-inbox/2026-11-06/0003-github-trending-agent-tools-conardli-garden-skills-14-114-175-d5b5]]"
title: "ConardLi/garden-skills ⭐ 14,114(今日 +175)"
url: https://github.com/ConardLi/garden-skills
source: github-trending-agent-tools
published_at: 2026-11-06T00:03:12.009832+00:00
fetched_at: 2026-11-06T00:14:54.245553+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一組可安裝到 Claude Code、Cursor 等 AI 編程代理的 Agent Skills 合集，涵蓋動態影片、網頁設計、圖像生成等。 **How** 提供 npx skills CLI、Claude Code 外掛市集、釘選版本的 .zip、手動複製與 git submodule 五種安裝方式，並可用 tag 鎖定特定 commit。 **What** 收錄 6 個技能：motion-showreel v0.1.0、web-video-presentation v1.2.2、web-design-engineer v1.3.0（25 個 recipe）、gpt-image-2 v1.0.4（公開案例庫 160 多個）、beautiful-article v0.1.0、kb-retriever v1.0.1。"
key_points:
  - "web-design-engineer 流程為先釐清產品脈絡、宣告設計系統、產出早期 v0，再完成整體體驗並驗證"
  - "gpt-image-2 支援本地生成、委派給宿主環境的圖像工具，或在無圖像工具時僅提供 prompt 建議模式"
  - "正式環境可用 tag 範圍的 tree/ URL 固定到發布時的 commit，而非追蹤 main 的最新版本"
tags: [agent-skills, claude-code, version-pinning, web-design, image-prompting]
topics: [agents.coding_agents, agents.frameworks]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## ConardLi/garden-skills ⭐ 14,114(今日 +175)

一組可安裝到 Claude Code、Cursor 等 AI 編程代理的 Agent Skills 合集，涵蓋動態影片、網頁設計、圖像生成等。

**How** 提供 npx skills CLI、Claude Code 外掛市集、釘選版本的 .zip、手動複製與 git submodule 五種安裝方式，並可用 tag 鎖定特定 commit。

**What** 收錄 6 個技能：motion-showreel v0.1.0、web-video-presentation v1.2.2、web-design-engineer v1.3.0（25 個 recipe）、gpt-image-2 v1.0.4（公開案例庫 160 多個）、beautiful-article v0.1.0、kb-retriever v1.0.1。

### 重點
- web-design-engineer 流程為先釐清產品脈絡、宣告設計系統、產出早期 v0，再完成整體體驗並驗證
- gpt-image-2 支援本地生成、委派給宿主環境的圖像工具，或在無圖像工具時僅提供 prompt 建議模式
- 正式環境可用 tag 範圍的 tree/ URL 固定到發布時的 commit，而非追蹤 main 的最新版本

**原文：** [github-trending-agent-tools](https://github.com/ConardLi/garden-skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ConardLi's open-source Skills collection, featuring web design, knowledge retrieval, image generation, and more.

Garden Skills

Table of contents

Install

Compatibility

What is a Skill?

Contributing

Acknowledgments

Connect

License

motion-showreel

web-video-presentation

web-design-engineer

gpt-image-2

beautiful-article

kb-retriever

Option A · skills CLI (npx)

Option B · Claude Code plugin marketplace

Option C · Pinned .zip from Releases

Option D · Manual copy into your project

Option E · Git submodule

A curated collection of production-ready Agent Skills for Claude Code, Cursor, Codex, and other AI coding agents.

 

English · 中文文档 · 日本語

Category: Motion Graphics / Code Video

Best for: showreels, product films, UI motion, kinetic typography, logo/title sequences, generative loops, retrospectives and narrated explainers. Short pieces typically run 5–60 s; chapter-based films support up to 20 minutes.

motion-showreel delivers MP4 plus editable source. It confirms the topic, duration, orientation, independent music/SFX sources and narration mode, then writes a brief and confirms style frames. Deterministic render(t) pages are captured frame by frame on a shared audio/picture timeline. Narration follows a user-supplied script or recording; pictures follow actual speech timings. Long films use persistent chapter caches and technical acceptance.

Highlights:

↑ 4-second excerpts of pieces made with the skill. Open the showcase for the full set, including the skill's own 80-second trailer and the style gallery.

Links: README · SKILL.md · Download v0.1.0 .zip

Category: Web Video / Presentation Engineering Best for: turning scripts, articles, lessons, product demos, and talks into click-driven 16:9 web presentations that can be screen-recorded as cinematic videos.

web-video-presentation builds record-ready Vite + React + TypeScript presentations that behave like video production surfaces. The workflow turns raw articles into narration scripts, maps script beats to full-screen scenes, pauses at required checkpoints, and can optionally synthesize narration audio after the visual outline is approved.

Highlights:

↑ All 23 themes at a glance — open the full gallery for live 16:9 previews, design signatures, and best-for tags.

Links: README · SKILL.md · Download v1.2.2 .zip

Category: Design / Frontend Best for: web pages, landing pages, dashboards, interactive prototypes, HTML slide decks, animations, UI mockups, data visualizations, and design-system explorations.

web-design-engineer turns AI-generated web artifacts from merely functional into polished, deliberate, and visually memorable front-end work. It treats the agent as a design engineer: first understanding product context, then declaring a design system, showing an early v0, building the full experience, and verifying the result.

Highlights:

↑ 12 of 25 anchored recipes — open the full gallery for all 25 working artefacts (apothecary pages, trading workstations, magazine covers, Y2K portals, mid-century posters ...) with signature moves and best-for tags.

Links: README · SKILL.md · Website · Demo · Download v1.3.0 .zip

Category: Image Generation / Prompt Engineering Best for: posters, UI mockups, product visuals, infographics, academic figures, technical diagrams, comics, avatars, storyboards, branding boards, and image-editing workflows.

gpt-image-2 is a focused image-generation skill for GPT Image 2 and OpenAI-compatible image APIs. It is designed to work across different agent environments: fully local Garden generation, host-native image-tool delegation, or prompt-only advisor mode when no image tool is available.

Highlights:

↑ 12 selected cases from the 160+ public case library — open the skill gallery for more templates, or browse the live website .

Links: README · SKILL.md · Website · Download v1.0.4 .zip

Category: Editorial · Any source → beautiful article Best for: turning URLs, PDFs, DOCX, Markdown, plain text, screenshots, and pasted notes into a polished, share-ready article — long-form, briefings, explainers, tutorials, post-mortems, visual essays, dialogue transcripts.

beautiful-article is an editorial harness skill: it does not just "make a webpage", it edits and designs the source material into a polished article that is easier to read, share, and archive than the original. The skill flows through a small source → plan → double-confirmation → build → final review → repair loop and pauses at three hard checkpoints so the user keeps editorial control over article type, theme, layout, image strategy, cover, and delivery format.

Highlights:

Links: README · SKILL.md · Download v0.1.0 .zip

Category: Retrieval / Local Knowledge Base Best for: answering questions from a local knowledge/ directory, searching structured documentation, and extracting evidence from Markdown, text, PDF, and Excel files without flooding the agent context.

kb-retriever is a local knowledge-base retriever built around careful, progressive search. Instead of loading whole files, it navigates hierarchical index files, narrows the candidate set, processes complex file types correctly, and answers with sources.

Highlights:

Links: README · SKILL.md · Download v1.0.1 .zip

There are five supported install paths. Pick the one that fits your stack:

Each skill section above also has a Download v .zip link in
its "Links:" row that points at the current pinned release artifact. Those
URLs are auto-rewritten by scripts/release/update-readme.mjs on every release, so they always advertise the latest immutable version.

The fastest agent-agnostic path. Uses the standard npx skills CLI ,
which auto-detects your agent (Claude Code, Cursor, Codex, etc.) and drops the
skill into the right directory.

Defaults to the latest commit on main . That's what you want 95% of the
time — the CLI tracks each skill's most recent published SKILL.md straight
from the source tree.

Want a pinned version? (CI / production) Use a tag-scoped tree/ URL —
this points at the exact commit a release was cut from:

For each skill, the current pinned .zip U

</details>