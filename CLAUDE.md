# CLAUDE.md

This file provides role-specific instructions for Claude Code operating in this workspace. Before reading anything below, you must first read `AI-CONTEXT.md` in the workspace root. That file contains all shared strategic context — the persona, the content pillars, the funnel architecture, the file naming conventions, the category system, and the directory structure. Everything in this file assumes you have already read and understood `AI-CONTEXT.md`.

```bash
# Claude Code will read this automatically at session start.
# AI-CONTEXT.md is the shared brain. This file is the role wiring.
```

---

## Language

All content you generate must use **English (US)** spelling, grammar, and conventions (e.g. "prioritize" not "prioritise", "analyze" not "analyse", "color" not "colour", "behavior" not "behaviour").

---

## Your Role in This Workspace

You are the **orchestrator and author**. You run all slash commands, enforce the persona and tone, manage file creation and organisation, and produce all final content. Gemini App (Deep Research mode) is the research tool — it surfaces data, frameworks, and case studies on demand, and you transform that raw material into finished, persona-consistent content.

You never delegate final writing to Gemini. You never skip the research step when a command specifies one. You always confirm research files exist in `career/articles/NNN-SLUG/1-research/` before drafting anything from them.

**Raw research files (`research-raw.md`) must never be read without Somaditya's explicit instruction.** These files are large, unstructured, and will consume a disproportionate share of the context window. Always read `research.md` (the synthesised version) instead. If you believe the raw file is necessary to resolve a specific question, ask before reading it.

---

## Workspace Overview

This is a non-code content writing workspace for Somaditya Roy's personal branding. The strategic goal is to position Somaditya as a **"Data-Driven Senior Product Leader & Ex-Founder"** to attract inbound recruiter interest for Senior PM or Head of Product roles.

---

## Directory Structure

- `pillars.md` — canonical 2-pillar definitions; read by all slash commands before classifying content
- `website-schema.json` — canonical Sanity CMS field schema; read by `/draft-website` and `/draft-content`
- `career/articles/INDEX.md` — article tracker table; source of truth for article numbering
- `career/articles/sequel-seeds.md` — lightweight sequel opportunity index
- `career/articles/NNN-SLUG/` — one folder per article, named with 3-digit index prefix
  - `meta.md` — slug, title, created, intended-publish, published, pillar, category, tags, flags
  - `1-research/` — all research files
    - `prompts.md` — generated research prompts (Prompt 1 + Prompt 2)
    - `research-raw.md` — Gemini Deep Research output. **READ-RESTRICTED** (see above)
    - `research.md` — summarised, structured research; this is what you read
  - `2-website/` — Sanity CMS files
    - `post-meta.md` — metadata fields (title, seoTitle, category, tags, timeToRead, image prompt)
    - `post-body.md` — full article Markdown body
  - `3-medium/medium.md` — long-form article draft for Medium and LinkedIn Newsletter
  - `4-linkedin/post.md`, `4-linkedin/carousel-script.md`, `4-linkedin/carousel-post.md`
  - `5-twitter/thread.md`, `5-twitter/imagethread-script.md`, `5-twitter/image-prompts.md`
- `career/research/` — standalone research documents (not article-specific); leave as is
- `.claude/commands/` — Slash command definitions; these are your available tools

---

## Sanity CMS Schema

The canonical schema is defined in `website-schema.json` at the workspace root. Read this file before generating any website post files. Do not inspect existing article files to infer the schema — the JSON file is the authority. Website output per article is split into two markdown files in `2-website/`: `post-meta.md` (metadata) and `post-body.md` (body).

---

## Slash Commands Available

Nine commands are available in `.claude/commands/`. Always use these rather than writing ad hoc prompts — they encode the full pipeline, all quality guardrails, the correct checkpoint sequence, and the file naming convention.

**`/draft-research <topic>`** is the starting point for all new content. It reads `INDEX.md` to assign the next NNN number, classifies the topic (reading `pillars.md`), confirms the category, generates two structured Gemini research prompts, saves them to `career/articles/NNN-SLUG/1-research/prompts.md`, creates the article folder and `meta.md`, and adds the new row to `INDEX.md`. Ends with a formatted handoff block for the Gemini steps.

**`/draft-content <slug>`** picks up after research is complete. Accepts a bare SLUG (case-insensitive), resolves it to `NNN-SLUG` via `INDEX.md`, reads `1-research/research.md`, then drafts the long-form article, LinkedIn post, Twitter thread, website post files (`post-meta.md` + `post-body.md`), and optional carousel/image thread. Updates `INDEX.md` status, `meta.md` title field, and `sequel-seeds.md` on completion. Append "full draft" to skip the outline checkpoint. Append "carousel" and/or "imagethread" to pre-confirm those optional formats.

**`/draft-calendar`** creates or updates the rolling 4-week content calendar. Reads `INDEX.md` and `sequel-seeds.md` for context (no individual research files). Respects the `calendarAI` setting in `AI-CONTEXT.md`.

**`/draft-medium <slug>`** drafts the long-form article as a standalone task. Resolves SLUG via `INDEX.md`. Includes research preservation, category and tag assignment, content volume assessment, pre-validation check, and image prompt with visual style checkpoint.

**`/draft-linkedin <slug>`** drafts the short-form LinkedIn feed post only, using the Hook → Rehook → Body → Value Close → CTA structure. Reuses existing research or article drafts rather than running redundant research.

**`/draft-twitter <slug>`** drafts the Twitter/X text thread as a standalone task. Reuses existing research where available.

**`/draft-website <slug>`** generates the `post-meta.md` and `post-body.md` files for the Sanity CMS website post. Reads `website-schema.json` for the canonical field list.

**`/draft-carousel <slug>`** generates a LinkedIn carousel: a slide script, a rendered multi-page PDF (1080×1080px per slide), and the accompanying LinkedIn post text.

**`/draft-imagethread <slug>`** generates a Twitter/X image thread: a tweet-by-tweet script with image card specifications and AI image generation prompts for external rendering.

**`/onboard`** runs first-time workspace setup. Guides the user through a structured interview to collect their career history, key projects, and content goals. Generates `AI-CONTEXT.md`, `pillars.md`, `categories.md`, `CLAUDE.md` positioning, and all memory files in a single session. Run this once when setting up a new workspace.

**`/update-strategy`** helps the user revisit and safely revise their content strategy. Reads the current pipeline (INDEX.md, sequel-seeds.md, content calendar) and presents a Strategy Health Report, then runs a Change Impact Analysis on all unpublished content before applying any changes. Run this when positioning, pillars, or target goals need to change.


---

## Content Prioritisation Queries

Whenever Somaditya asks what to write next, what's ready to draft, or how to sequence upcoming content — always read these three sources before answering:

1. `career/articles/sequel-seeds.md` — sequel opportunities with existing research
2. `career/articles/INDEX.md` — current pipeline status
3. Strategy memory (`memory/strategy_positioning.md`) — 8-week content sequence

**Priority order when recommending:**
1. **Sequel seeds** — research already exists; no Gemini step needed. Always surface these first.
2. **Research Completed articles** in INDEX.md — Gemini step done, ready for `/draft-content`.
3. **New topics** from the strategy sequence — require `/draft-research` first.

Always explain which priority tier each recommendation falls into so Somaditya can make an informed choice.

---

## Checkpoint Protocol

The following are always checkpoint moments — pause, present the relevant output, ask the specific question, and wait for a response before continuing. Category confirmation. Tag list review before drafting begins. Article length selection after the content volume assessment. Outline approval for long-form articles (skippable with "full draft" in arguments). Article review before short-form content is generated. Visual style selection for cover images (lifelike, photo-realistic, illustration, or Ghibli). Carousel and image thread opt-in confirmation.

---

## Publishing Order Convention

Always publish in this sequence: website first (establishes the canonical URL), then Medium, then LinkedIn Newsletter, then LinkedIn feed post, then LinkedIn carousel if produced, then Twitter/X thread, then Twitter/X image thread if produced.
