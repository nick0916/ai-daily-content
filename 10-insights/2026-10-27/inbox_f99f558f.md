---
id: inbox_f99f558f
date: 2026-10-27
source_ref: "[[00-inbox/2026-10-27/2338-github-trending-agent-tools-elayadesign-ai-design-skills-9-250-1-395-699b]]"
title: "elayadesign/ai-design-skills ⭐ 9,250(今日 +1,395)"
url: https://github.com/elayadesign/ai-design-skills
source: github-trending-agent-tools
published_at: 2026-10-27T23:38:40.836858+00:00
fetched_at: 2026-10-27T23:51:31.212477+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "給 AI 寫程式工具用的一組設計規範技能，讓模型照既定視覺風格產出介面。 **How** 每個 skill 是獨立資料夾，核心為 SKILL.md；字型、顏色、間距、動效等設計值集中在檔案底部一段，fork 後修改即可套用到整個 skill。 **What** 支援 Claude Code、Cursor、Codex、Windsurf 等能讀 markdown 規則檔的工具；landing-page-design 改編自 Leonxlnx/taste-skill（MIT）；本專案為 MIT 授權，GitHub 星數 9,250（今日 +1,395）。"
key_points:
  - "每個 skill 是獨立資料夾，複製 SKILL.md 到 .claude/skills 或 .cursor/rules 即可使用"
  - "設計值（字型、顏色、間距、動效）集中在 SKILL.md 底部一段，fork 後修改即可"
  - "landing-page-design 改編自 Leonxlnx/taste-skill（MIT），文件末尾列出出處"
tags: [claude-code, cursor, agent-skills, design-system, landing-page]
topics: [agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## elayadesign/ai-design-skills ⭐ 9,250(今日 +1,395)

給 AI 寫程式工具用的一組設計規範技能，讓模型照既定視覺風格產出介面。

**How** 每個 skill 是獨立資料夾，核心為 SKILL.md；字型、顏色、間距、動效等設計值集中在檔案底部一段，fork 後修改即可套用到整個 skill。

**What** 支援 Claude Code、Cursor、Codex、Windsurf 等能讀 markdown 規則檔的工具；landing-page-design 改編自 Leonxlnx/taste-skill（MIT）；本專案為 MIT 授權，GitHub 星數 9,250（今日 +1,395）。

### 重點
- 每個 skill 是獨立資料夾，複製 SKILL.md 到 .claude/skills 或 .cursor/rules 即可使用
- 設計值（字型、顏色、間距、動效）集中在 SKILL.md 底部一段，fork 後修改即可
- landing-page-design 改編自 Leonxlnx/taste-skill（MIT），文件末尾列出出處

**原文：** [github-trending-agent-tools](https://github.com/elayadesign/ai-design-skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AI Design Skills

Skills

Install

Make it yours

Credits

License

A growing collection of design skills for AI coding tools — Claude Code, Cursor, Codex, Windsurf, and anything else that reads a markdown rules file.

Each skill is a self-contained folder. Install the ones you need.

More on the way. Upgrading an existing site instead of building new? That one lives in its own repo since it predates this collection.

Pick a skill from the table above, then swap below for its folder name.

Then just ask, in plain language, for what that skill covers.

Or paste the file into Settings → Rules for AI .

Copy the skill's SKILL.md into whatever your tool uses for project rules:

Download the skill's SKILL.md and upload it to a Project, or attach it to a chat and say "follow this."

Every skill's design values (fonts, colors, spacing, motion) live in one section near the bottom of its file. Fork this repo, edit that section, and the rest of the skill follows automatically.

landing-page-design adapts content realism and motion ideas from Leonxlnx/taste-skill by Leon Lin, MIT licensed. Details are at the end of its SKILL.md .

MIT. Use it, fork it, ship it, sell what you build with it. No attribution needed.

mkdir -p .claude/skills
git clone https://github.com/elayadesign/ai-design-skills.git /tmp/ai-design-skills
cp -r /tmp/ai-design-skills/skills/ .claude/skills/

mkdir -p .cursor/rules
curl -o .cursor/rules/ .md \
 https://raw.githubusercontent.com/elayadesign/ai-design-skills/main/skills/ /SKILL.md

</details>