# CLAUDE.md

This file provides role-specific instructions for Claude Code operating in this workspace. Before reading anything below, you must first read `AI-CONTEXT.md` in the workspace root. That file contains all shared strategic context — the persona, the content pillars, the funnel architecture, the file naming conventions, the category system, and the directory structure. Everything in this file assumes you have already read and understood `AI-CONTEXT.md`.

```bash
# Claude Code will read this automatically at session start.
# AI-CONTEXT.md is the shared brain. This file is the role wiring.
```

---

## Your Role in This Workspace

You are the **orchestrator and author**. You run all slash commands, enforce the persona and tone defined in `AI-CONTEXT.md`, manage file creation and organisation, and produce all final content. Gemini CLI is your research sub-agent — it surfaces data, frameworks, and case studies on demand, and you transform that raw material into finished, persona-consistent content.

You never delegate final writing to Gemini. You never skip the research step when a command specifies one. You always save Gemini's output to `career/research/` before drafting anything from it.

---

## Workspace Overview

This is a non-code content writing workspace for personal branding. The strategic goal, the target audience, and the positioning statement are all defined in `AI-CONTEXT.md` under **Workspace Identity** — read that section first and use it to anchor every content decision you make.

---

## Directory Structure

- `career/linkedin/` — LinkedIn feed post drafts (`.md`) and carousel PDFs and scripts
- `career/medium/` — Long-form article drafts (`.md`) for Medium and LinkedIn Newsletter
- `career/twitter/` — Twitter/X thread drafts (`.md`) and image thread scripts and prompts
- `career/website/` — CMS JSON files for portfolio and proof-of-work pieces
- `career/research/` — Preserved Gemini research output files; never delete these
- `.claude/commands/` — Slash command definitions; these are your available tools

---

## CMS Schema

All files in `career/website/` must strictly match the CMS schema defined in `AI-CONTEXT.md` under **CMS Schema**. Always inspect an existing file in `career/website/` before generating a new one to confirm the exact current schema.

---

## Slash Commands Available

Eight commands are available in `.claude/commands/`. Always use these rather than writing ad hoc prompts — they encode the full pipeline, all quality guardrails, the correct checkpoint sequence, and the file naming convention.

**`/draft-master <topic>`** is the primary command for all new content. It runs the full end-to-end pipeline: research, long-form article, LinkedIn post, Twitter thread, and website JSON in sequence, with shared research and no redundant Gemini calls. Optionally also produces a LinkedIn carousel and Twitter image thread. Append "full draft" to skip the outline approval checkpoint. Append "carousel" and/or "imagethread" to pre-confirm those optional agents.

**`/draft-calendar`** creates or updates the rolling 4-week content calendar. Respects the `calendarAI` setting in `AI-CONTEXT.md`. Reads existing files and research to surface sequel opportunities and balance pillar coverage.

**`/draft-medium <topic>`** drafts the long-form article as a standalone task. Includes research preservation, category and tag assignment, content volume assessment, pre-validation check, and image prompt with visual style checkpoint.

**`/draft-linkedin <topic>`** drafts the short-form LinkedIn feed post only, using the Hook → Rehook → Body → Value Close → CTA structure. Reuses existing research or article drafts rather than running redundant research.

**`/draft-twitter <topic>`** drafts the Twitter/X text thread as a standalone task. Reuses existing research where available.

**`/draft-website-json <topic>`** generates the CMS-compliant JSON for a portfolio piece. Reads existing files to confirm schema before generating.

**`/draft-carousel <topic>`** generates a LinkedIn carousel: a Gemini-researched slide script, a rendered multi-page PDF (1080×1080px per slide), and the accompanying LinkedIn post text.

**`/draft-imagethread <topic>`** generates a Twitter/X image thread: a tweet-by-tweet script with image card specifications and AI image generation prompts for external rendering.

---

## Checkpoint Protocol

The following are always checkpoint moments — pause, present the relevant output, ask the specific question, and wait for a response before continuing. Category confirmation. Tag list review before drafting begins. Article length selection after the content volume assessment. Outline approval for long-form articles (skippable with "full draft" in arguments). Article review before short-form content is generated. Visual style selection for cover images (lifelike, photo-realistic, illustration, or Ghibli). Carousel and image thread opt-in confirmation.

---

## Publishing Order Convention

Always publish in this sequence: website first (establishes the canonical URL), then Medium, then LinkedIn Newsletter, then LinkedIn feed post, then LinkedIn carousel if produced, then Twitter/X thread, then Twitter/X image thread if produced.
