# AI-CONTEXT.md — Shared Workspace Context

This file is the single source of truth for all strategic, structural, and operational knowledge about this workspace. Both Claude Code and Gemini CLI are instructed to read this file at the start of every session before acting on any task. Neither tool should rely solely on its own role-specific briefing file (CLAUDE.md or GEMINI.md) for workspace knowledge — those files only contain role-specific wiring. Everything about *what this workspace is and how it works* lives here.

If you are Claude Code, read this file in full, then return to CLAUDE.md for your role-specific instructions.
If you are Gemini CLI, read this file in full, then return to GEMINI.md for your role-specific instructions.

---

## Workspace Identity

This is a **non-code content writing workspace** for Somaditya Roy's personal branding. The strategic goal is to position Somaditya as a **BA making the deliberate move to PM — honest about the transition** — to attract inbound recruiter interest for Associate PM or PM roles where his decade of product-adjacent delivery work is recognised.

The positioning statement is: *"I've been doing product management for 10 years. My title just hasn't said so."*

The content produced here is not generic thought leadership. It is high-signal, practitioner-level material grounded in real delivery outcomes, real product decisions, and real founder experience (MoneTask Labs). The transition IS the story — content should make the case that the gap between Somaditya's work and his title is the recruiter's opportunity, not a liability. Every piece should be traceable to a real outcome, a real constraint, or a real decision made under pressure.

> **Not set up yet?** Run `/onboard` to personalise this workspace. The command guides you through a structured interview and populates all placeholders with your own positioning, career history, and content pillars.

---

## Persona & Tone

**Positioning statement:** *"I've been doing product management for 10 years. My title just hasn't said so."*

**Tone:** Direct, honest, specific, self-aware. The transition is not a weakness to be hidden — it is the central argument. Never performs a title not held. No hedging language ("it might be worth considering"). No generic PM-101 observations. No "As a PM I've learned that…" openers. Every claim should be traceable to a real outcome, a real data point, or a real decision made under pressure.

**Voice characteristics:** Direct. Specific. Grounded in lived experience. Willing to name the gap between title and work explicitly, because that gap is the proof of capability. Comfortable naming real tools, real constraints, and real tradeoffs. References MoneTask Labs, Express Scripts, LatentView, and TCS where they strengthen the point — not as name-dropping, but as evidence. Recruiter scepticism about the BA-to-PM move is anticipated and answered, not avoided.

---

## The Two Content Pillars

All content produced in this workspace must fall into exactly one of the following two pillars. This constraint is intentional — the LinkedIn algorithm rewards semantic focus, meaning 80% of content should orbit a tightly defined topic cluster. Spreading across too many unrelated topics dilutes algorithmic authority.

**Pillar 1 — Shipping Without the Title:** Everything that demonstrates PM-level work done under non-PM titles. Express Scripts product stories, LatentView delivery leadership, TCS systems work, MoneTask lessons. This pillar answers the recruiter sceptic directly: "Why hire a BA into PM?" — by showing that the work was already PM work, the title just was not. Topics include stakeholder alignment, data-informed decision-making, requirements translation, delivery ownership, and founder-mode execution.

**Pillar 2 — Building Catalyst:** Build-in-public content around the Catalyst app. Real product decisions, real tradeoffs, MVP scoping, user research findings, and the honest reasoning behind each choice. This pillar documents the transition in real time — not claimed expertise, but visible work. It ends with a demo video post that becomes the bottom-funnel case study. When Catalyst ships, it is the proof that closes the argument the rest of the content makes.

> **Machine-readable definitions:** The canonical pillar definitions used by all slash commands are in `pillars.md` at the workspace root. Update that file (not this section) when the pillar strategy changes.

---

## Content Funnel Architecture

All content exists within a three-layer funnel. Every piece belongs to one layer, and the calendar should be balanced with roughly 60% middle layer, 30% top layer, and 10% bottom layer.

The **top layer (awareness)** contains content that a cold audience can immediately understand and interact with. Short LinkedIn posts, Twitter threads, and broadly framed carousels live here. These establish who Somaditya is. They are not expected to convert — their job is reach and first impressions.

The **middle layer (education / consideration)** is the most strategically important layer. Long-form articles, LinkedIn Newsletter editions, named-framework carousels, and deep infographics live here. People experiencing this layer are encountering Somaditya's specific methodology and practitioner thinking. The algorithm rewards this layer with saves, which are the highest-value engagement signal. Research shows people need five to seven exposures to a personal brand before they act — this layer delivers those repeated, memorable impressions.

The **bottom layer (conversion)** closes. Case studies from MoneTask Labs, portfolio pieces on the website, and proof-of-work JSON files live here. This layer will not perform well in raw engagement metrics — that is expected and acceptable. It speaks to an audience that has already been warmed up by the top two layers and is now evaluating whether to reach out. Never judge a conversion piece by its likes or shares.

---

## LinkedIn Algorithm

The LinkedIn algorithm as of 2025–2026 operates as a semantic AI model. Its key behaviours that affect how content should be written and structured are as follows.

It reads content semantically rather than relying on explicit engagement signals. This means keyword stuffing no longer works, but genuine topical depth does. It gives three to five times more processing weight to the first sentence of a post than to any other line — making the hook the single highest-leverage element in any piece of short-form content. It prioritises saves over likes and comments, which means content designed to be referenced later (frameworks, checklists, named methodologies) outperforms content designed to provoke reactions. It rewards depth and dwell time — longer, more substantive content that keeps readers engaged longer performs better than short content that gets skimmed. And it penalises topical inconsistency — accounts that post about unrelated subjects in the same period receive lower distribution on all their content.

---

## Post Structure: Hook → Rehook → Body → Value Close → CTA

All LinkedIn feed posts must follow this five-part structure. Each part has a specific job that cannot be delegated to another.

The **Hook** is the first line only. It appears before the "…see more" cutoff and must stop the scroll entirely on its own. Use a contrarian claim, a striking specific statistic with its implication, or a scenario the reader will immediately recognise from their own experience. Never open with "I" as the first word. Never open with a question.

The **Rehook** is lines two and three. It does not answer the hook — it deepens the curiosity. The hook opens a door; the rehook reveals something unexpected behind it. This is the element most posts omit, and its absence is the difference between a post that gets opened and one that gets saved.

The **Body** is the value delivery. A reusable framework, a structured teardown, or a checklist that makes the reader want to save the post for reference. Single-sentence paragraphs with line breaks between them. Bold key framework terms.

The **Value Close** is one or two lines immediately before the CTA. It crystallises the single most important takeaway into a standalone sentence — the thing a reader would screenshot even if they skip everything else.

The **CTA** drives the reader off LinkedIn to an owned asset. This is the deplatforming step — every post is an opportunity to move readers to a channel Somaditya owns and controls, independent of any algorithm.

---

## Deplatforming Convention

Every piece of content — regardless of format — must include a CTA that moves the reader toward an owned asset. The owned assets in order of preference are: the personal website (canonical URL, SEO-indexed, full reader experience), the newsletter or email list (direct access, no algorithm), and Medium (high domain authority, but not fully owned). LinkedIn Newsletter sits between owned and rented. Twitter/X is always rented.

Every CTA should feel like it is offering something more valuable than what the reader just consumed — not "see more" but "the full framework is there, not here."

---

## Carousel Strategy

LinkedIn carousels are uploaded as multi-page PDFs. Each page becomes a swipeable slide in the feed. Carousels and infographics are the highest-converting formats for follower growth on LinkedIn — not just the highest-engagement formats. The reason is behavioural: readers spend more time on carousels digesting and saving them, which triggers a follow. Video drives views but not follows at the same rate.

The strategic goal of every carousel is twofold: immediate saves (authority signal) and follower conversion (compounding reach).

Carousels are most effective when the topic has a named framework with four to eight clearly separable components, because each component becomes its own slide. The five supported narrative structures are: Problem → Solution (for contrarian or misconception topics), Step-by-Step Guide (for execution playbooks), Before → After (for case studies), Myth vs. Fact (for debunking topics), and Data Story (for data-heavy frameworks).

---

## Pre-Validation Principle

When selecting a content angle or framework to feature, prefer angles that can be pre-validated — meaning there is already evidence that this type of content resonates with a similar-sized audience on LinkedIn or elsewhere. Pre-validation does not mean copying. It means studying what has already performed well on comparable accounts, identifying the structural reason it worked, and then building a new piece that applies that same logic to Somaditya's own experiences, data, and perspective. The framework gets a new name. The examples come from MoneTask Labs or his PM career. The insight is genuinely his own.

---

## LinkedIn Profile as a Landing Page

The LinkedIn profile should be treated as a conversion asset, not a CV. The most important structural principle is keyword alignment: the primary positioning keywords must appear consistently in the header, About section, job titles, and work experience descriptions. The algorithm reads profiles semantically — inconsistent keywords across sections actively hurts discoverability.

Work experience descriptions must include measurable outcomes, not just responsibilities. Quantified results ("reduced reporting time by 40%") outperform task descriptions ("built dashboards") with both the algorithm and recruiters.

---

## Directory Structure

```
workspace-root/
├── AI-CONTEXT.md               ← this file; single source of truth for both AIs
├── CLAUDE.md                   ← Claude Code role-specific instructions
├── GEMINI.md                   ← Gemini CLI role-specific instructions
├── pillars.md                  ← canonical pillar definitions (read by all slash commands)
├── website-schema.json         ← canonical Sanity CMS field schema (read by /draft-website and /draft-content)
├── categories.md               ← living category registry; single source of truth for all categories
├── README.md                   ← operator reference guide
├── career/
│   ├── articles/
│   │   ├── INDEX.md            ← article tracker: all articles, statuses, and meta info
│   │   ├── sequel-seeds.md     ← lightweight sequel opportunity index (updated by /draft-content)
│   │   └── NNN-SLUG/           ← NNN is a zero-padded 3-digit index number (e.g. 001-monetask-18-months-never-shipped)
│   │       ├── meta.md         ← slug, title, created, intended-publish, published, pillar, category, tags, flags
│   │       ├── 1-research/     ← all research files for this article
│   │       │   ├── prompts.md          ← generated research prompts (Prompt 1 + Prompt 2)
│   │       │   ├── research-raw.md     ← Gemini Deep Research output (READ-RESTRICTED)
│   │       │   └── research.md         ← summarised, structured research (the version Claude reads)
│   │       ├── 2-website/      ← Sanity CMS website post files
│   │       │   ├── post-meta.md        ← title, seoTitle, category, tags, timeToRead, image prompt
│   │       │   └── post-body.md        ← full article Markdown (same content as medium.md at time of generation)
│   │       ├── 3-medium/       ← long-form article for Medium and LinkedIn Newsletter
│   │       │   └── medium.md
│   │       ├── 4-linkedin/     ← all LinkedIn content for this article
│   │       │   ├── post.md
│   │       │   ├── carousel-script.md
│   │       │   └── carousel-post.md
│   │       └── 5-twitter/      ← all Twitter/X content for this article
│   │           ├── thread.md
│   │           ├── imagethread-script.md
│   │           └── image-prompts.md
│   └── research/               ← standalone research documents (not article-specific)
│       └── prompts/            ← empty after article prompts moved into article folders
└── .claude/
    └── commands/               ← slash command definitions for Claude Code
        ├── draft-research.md
        ├── draft-content.md
        ├── draft-calendar.md
        ├── draft-medium.md
        ├── draft-linkedin.md
        ├── draft-twitter.md
        ├── draft-website.md
        ├── draft-carousel.md
        └── draft-imagethread.md
```

---

## File Naming Convention

Every article lives in a folder at `career/articles/NNN-SLUG/`, where NNN is a zero-padded 3-digit sequential index number and SLUG is a kebab-case topic slug of 5–6 words that precisely describes the article's angle. For example: `career/articles/006-north-star-metric-b2b-saas/`. The NNN prefix is assigned automatically by `/draft-research` by reading the last # in `career/articles/INDEX.md` and incrementing by one.

Files inside the article folder use simple names within their numbered subfolders — `3-medium/medium.md`, `2-website/post-meta.md` — because they are already scoped by the folder structure.

**Slug resolution in commands:** All slash commands accept a bare `SLUG` (case-insensitive). They normalize to lowercase and look up `INDEX.md` to find the full `NNN-SLUG` folder. Typing `Monetask-18-Months-Never-Shipped` resolves to `002-monetask-18-months-never-shipped`.

**Sanity CMS export:** At export time, assemble `post-meta.md` (frontmatter fields) and `post-body.md` (body content) into a JSON file matching the schema in `website-schema.json`. Rename the assembled JSON to `DATE_SLUG.json` using the `created` date from `meta.md` before uploading. This step is noted in the publishing checklist.

The research prompts file is saved inside each article folder: `career/articles/NNN-SLUG/1-research/prompts.md`.

---

## Category Registry

The file `categories.md` at the workspace root is the single source of truth for all content categories. Every published piece must have exactly one category drawn from the Active Categories list in that file. Categories are used directly by the website's filter UI — they must be consistent and never invented ad hoc. New categories are only added through an explicit approval checkpoint during a draft command: Claude Code proposes, pauses for confirmation, and only then adds the new category to `categories.md`.

---

## Tag Ordering Convention

Tags across all content must be ordered from most to least relevant using this consistent logic. The first tag is the primary topic keyword. Tags two and three are the primary methodology or framework featured. Tags four through six are supporting domain concepts. Remaining tags are adjacent context topics. All tags must be lowercase with hyphens for multi-word terms and must use real practitioner vocabulary. Generic tags like `product-management` or `pm-tips` should never appear.

---

## Research Preservation Policy

All research output must be saved inside the article's `1-research/` subfolder immediately before any drafting begins. Two research files exist per article:

- `career/articles/NNN-SLUG/1-research/research-raw.md` — the raw Gemini Deep Research output. **READ-RESTRICTED:** Claude Code must not read this file unless Somaditya explicitly instructs it to. It is large and unstructured and will consume a disproportionate share of the context window.
- `career/articles/NNN-SLUG/1-research/research.md` — the summarised, structured version that Claude reads for all drafting work.

Before starting a new research cycle, always check whether `career/articles/NNN-SLUG/1-research/research.md` already exists. If it does, load it rather than repeating the research process. After an article is drafted, a Research Utilisation Summary is appended to `research.md`, listing what was used and what is available for sequels. The SEQUEL SEEDS from that summary are also extracted and appended to `career/articles/sequel-seeds.md`.

---

## Article Length Strategy

The default target is 1,200–1,800 words (a 6–9 minute read). When research contains significantly more material than this target can accommodate, the master pipeline presents three options: a single article at the default length with surplus noted for sequels, a longer piece at 2,000–2,500 words, or a Part 1 now with a Part 2 later. Article length is always determined after seeing the research, never before.

---

## Sanity CMS Schema

The canonical Sanity CMS schema is defined in `website-schema.json` at the workspace root. This file lists every required field with its name, data type, and description. It is the authority — do not inspect existing article files to infer the schema. Update `website-schema.json` directly when the Sanity schema changes.

Each article's website output lives in `career/articles/NNN-SLUG/2-website/` as two files:
- `post-meta.md` — frontmatter with all metadata fields plus a Cover Image Prompt section
- `post-body.md` — the full article body in Markdown

At export time, assemble these into a JSON object matching `website-schema.json` and rename to `DATE_SLUG.json` before uploading to Sanity CMS.

---

## AI Configuration Settings

```
calendarAI: claude
```

`calendarAI` controls which AI generates content calendar ideas. Set to `claude` to always use Claude Code's reasoning, `gemini` to always delegate ideation to Gemini CLI, or `ask` (the default) to be prompted for a choice at the start of each calendar session.
