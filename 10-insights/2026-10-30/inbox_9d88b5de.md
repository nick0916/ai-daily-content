---
id: inbox_9d88b5de
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/2252-github-trending-agent-tools-anthropics-skills-185-265-287-e91b]]"
title: "anthropics/skills ⭐ 185,265(今日 +287)"
url: https://github.com/anthropics/skills
source: github-trending-agent-tools
published_at: 2026-10-30T22:52:43.221412+00:00
fetched_at: 2026-10-30T22:59:57.881023+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把可重複的專業流程寫成資料夾內的指示檔，讓 Claude 需要時再動態載入。 **Why** Claude 要在特定任務上表現更穩定，需要一種能重複套用的流程交付方式。 **How** 每個 skill 是一個資料夾，內含 SKILL.md（YAML frontmatter 只需 name 與 description 兩欄）以及指示、腳本與資源，Claude 依情境載入。 **What** 這是 Anthropic 官方的 Agent Skills 範例庫，分為創作設計、開發技術、企業溝通與文件類；docx、pdf、pptx、xlsx 為 source-available 非開源，其餘多為 Apache 2.0。可用 `/plugin marketplace add anthropics/skills` 註冊，也可透過 Claude API 使用或上傳自訂 skill。"
key_points:
  - "SKILL.md 的 frontmatter 只需 name（小寫、連字號）與 description（說明功能與使用時機）兩欄"
  - "docx、pdf、pptx、xlsx 文件類 skills 為 source-available 非開源，其餘範例多為 Apache 2.0"
  - "安裝方式：/plugin marketplace add anthropics/skills，再 /plugin install document-skills@anthropic-agent-skills"
tags: [agent-skills, claude-code, claude-api, plugin-marketplace, open-source]
topics: [agents.frameworks, foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## anthropics/skills ⭐ 185,265(今日 +287)

把可重複的專業流程寫成資料夾內的指示檔，讓 Claude 需要時再動態載入。

**Why** Claude 要在特定任務上表現更穩定，需要一種能重複套用的流程交付方式。

**How** 每個 skill 是一個資料夾，內含 SKILL.md（YAML frontmatter 只需 name 與 description 兩欄）以及指示、腳本與資源，Claude 依情境載入。

**What** 這是 Anthropic 官方的 Agent Skills 範例庫，分為創作設計、開發技術、企業溝通與文件類；docx、pdf、pptx、xlsx 為 source-available 非開源，其餘多為 Apache 2.0。可用 `/plugin marketplace add anthropics/skills` 註冊，也可透過 Claude API 使用或上傳自訂 skill。

### 重點
- SKILL.md 的 frontmatter 只需 name（小寫、連字號）與 description（說明功能與使用時機）兩欄
- docx、pdf、pptx、xlsx 文件類 skills 為 source-available 非開源，其餘範例多為 Apache 2.0
- 安裝方式：/plugin marketplace add anthropics/skills，再 /plugin install document-skills@anthropic-agent-skills

**原文：** [github-trending-agent-tools](https://github.com/anthropics/skills)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Public repository for Agent Skills

Skills

About This Repository

Skill Sets

Try in Claude Code, Claude.ai, and the API

Creating a Basic Skill

Partner Skills

Disclaimer

Claude Code

Claude.ai

Claude API

Note: This repository contains Anthropic's implementation of skills for Claude. For information about the Agent Skills standard, see agentskills.io .

Skills are folders of instructions, scripts, and resources that Claude loads dynamically to improve performance on specialized tasks. Skills teach Claude how to complete specific tasks in a repeatable way, whether that's creating documents with your company's brand guidelines, analyzing data using your organization's specific workflows, or automating personal tasks.

For more information, check out:

This repository contains skills that demonstrate what's possible with Claude's skills system. These skills range from creative applications (art, music, design) to technical tasks (testing web apps, MCP server generation) to enterprise workflows (communications, branding, etc.).

Each skill is self-contained in its own folder with a SKILL.md file containing the instructions and metadata that Claude uses. Browse through these skills to get inspiration for your own skills or to understand different patterns and approaches.

Many skills in this repo are open source (Apache 2.0). We've also included the document creation & editing skills that power Claude's document capabilities under the hood in the skills/docx , skills/pdf , skills/pptx , and skills/xlsx subfolders. These are source-available, not open source, but we wanted to share these with developers as a reference for more complex skills that are actively used in a production AI application.

These skills are provided for demonstration and educational purposes only. While some of these capabilities may be available in Claude, the implementations and behaviors you receive from Claude may differ from what is shown in these skills. These skills are meant to illustrate patterns and possibilities. Always test skills thoroughly in your own environment before relying on them for critical tasks.

You can register this repository as a Claude Code Plugin marketplace by running the following command in Claude Code:

Then, to install a specific set of skills:

Alternatively, directly install either Plugin via:

After installing the plugin, you can use the skill by just mentioning it. For instance, if you install the document-skills plugin from the marketplace, you can ask Claude Code to do something like: "Use the PDF skill to extract the form fields from path/to/some-file.pdf "

These example skills are all already available to paid plans in Claude.ai.

To use any skill from this repository or upload custom skills, follow the instructions in Using skills in Claude .

You can use Anthropic's pre-built skills, and upload custom skills, via the Claude API. See the Skills API Quickstart for more.

Skills are simple to create - just a folder with a SKILL.md file containing YAML frontmatter and instructions. You can use the template-skill in this repository as a starting point:

The frontmatter requires only two fields:

The markdown content below contains the instructions, examples, and guidelines that Claude will follow. For more details, see How to create custom skills .

Skills are a great way to teach Claude how to get better at using specific pieces of software. As we see awesome example skills from partners, we may highlight some of them here:

What are skills?

Using skills in Claude

How to create custom skills

Equipping agents for the real world with Agent Skills

./skills : Skill examples for Creative & Design, Development & Technical, Enterprise & Communication, and Document Skills

./spec : The Agent Skills specification

./template : Skill template

Select Browse and install plugins

Select anthropic-agent-skills

Select document-skills or example-skills

Select Install now

name - A unique identifier for your skill (lowercase, hyphens for spaces)

description - A complete description of what the skill does and when to use it

Notion - Notion Skills for Claude

/plugin marketplace add anthropics/skills

/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills

--- name : my-skill-name description : A clear description of what this skill does and when to use it --- # My Skill Name [ Add your instructions here that Claude will follow when this skill is active ] ## Examples - Example usage 1 - Example usage 2 ## Guidelines - Guideline 1 - Guideline 2

</details>