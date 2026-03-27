# Personal Branding Content Workspace — Operator Guide

This document is your personal reference for operating, maintaining, and updating this workspace. It assumes you are already familiar with the project's purpose. If you are returning after a gap and need a refresher on the strategic context, read `AI-CONTEXT.md` first.

---

## What This Is

This workspace is an opinionated content pipeline for building a personal brand through high-signal, practitioner-level writing. It is designed for professionals who want to create consistent, well-researched content without the overhead of managing a disconnected set of tools and prompts.

The system has three core principles:

1. **Research is preserved.** Gemini Deep Research output is saved inside each article folder. Sequel articles reuse the same research — no redundant Gemini calls.

2. **One command, all formats.** A single `/draft-content` command produces a long-form article, LinkedIn post, Twitter thread, and website files in one pass. Standalone commands exist for when you need only one format.

3. **Strategy is version-controlled.** Your content pillars, categories, and positioning live in files that the AI reads on every session. Changing your strategy means editing a file — not re-briefing the AI each time.

The pipeline uses Claude Code as the orchestrator and author, and Gemini App's Deep Research mode as the research tool. Neither tool tries to do the other's job.

---

## What This Workspace Does

This workspace produces the full content pipeline for your personal brand as a Data-Driven Senior PM and Ex-Founder. Given a topic or angle, it produces a long-form article, a LinkedIn feed post, a Twitter thread, Sanity CMS website post files, and optionally a LinkedIn carousel and Twitter image thread.

The pipeline has a deliberate manual break in the middle. Claude generates structured research prompts, you run them in Gemini App's Deep Research mode, then Claude takes the research and produces all the content. Research is preserved inside the article folder so sequel articles don't require re-running Gemini.

---

## Prerequisites — Get These Ready

Before running `/onboard`, have the following available:

- **Claude Code** installed and running (see [claude.ai](https://claude.ai))
- **Gemini App** with access to Deep Research mode (for the research step)
- **Your resume or CV** — even a rough draft; used to extract career history during onboarding
- **Your LinkedIn About section** — if you have one
- **A list of your most significant projects** — including side projects or ventures that didn't ship, with outcomes and metrics where you have them
- **Your current or most recent job title and employer**
- **Your target role or goal** — what you're trying to attract (a job, clients, an audience)
- **Sanity CMS project** *(optional)* — only needed if you want to use the website post output feature

You do not need to prepare any files before running `/onboard`. The command collects everything through a structured interview.

---

## Getting Started — Onboarding

**Step 1 — Clone or download this repository.**

```
git clone <repo-url>
cd content-writing
```

**Step 2 — Open the folder in Claude Code.**

```
claude
```

**Step 3 — Run `/onboard`.**

This is the only command you need to run on a fresh workspace. It will:

- Ask you to have your resume and project list ready
- Run a structured interview covering your career history, key projects, and content goals
- Derive two content pillars from your career narrative (with your approval before writing anything)
- Generate starter categories for your content registry
- Populate `AI-CONTEXT.md`, `pillars.md`, `categories.md`, and `CLAUDE.md` with your specific context
- Create your memory files so Claude maintains context across sessions

The whole process takes 20–30 minutes depending on how much career history you share.

**Step 4 — Review the generated files.**

After onboarding, open `AI-CONTEXT.md` and `pillars.md` and confirm they accurately reflect your positioning and the two content pillars Claude derived. These files drive every draft command — it's worth reading them once before you start publishing.

**Step 5 — Start your first article.**

```
/draft-research your-first-topic
```

---

## The Two-Phase Workflow

**Phase 1 — Research**

Run `/draft-research <topic>` in Claude Code. Claude will:
1. Read `INDEX.md` to assign the next NNN number to the article
2. Classify the topic into a content pillar (reading `pillars.md`)
3. Confirm a category (checkpoint)
4. Generate two research prompts and save them to `career/articles/NNN-SLUG/1-research/prompts.md`
5. Create the article folder at `career/articles/NNN-SLUG/` with `meta.md`
6. Add the new row to `INDEX.md` with status "Folder Created"
7. Output a handoff block telling you exactly what to do in Gemini

You then take Prompt 1 into Gemini App → Deep Research mode, save the output as `career/articles/NNN-SLUG/1-research/research-raw.md`, run Prompt 2 in a new Gemini conversation with the raw output pasted at the end, and save that output as `career/articles/NNN-SLUG/1-research/research.md`.

**Phase 2 — Content**

Run `/draft-content <slug>` in Claude Code (bare SLUG, case-insensitive — e.g., `monetask-18-months-never-shipped`). Claude will resolve it to the `NNN-SLUG` folder via `INDEX.md`, read `1-research/research.md`, and produce:
- Long-form article (`3-medium/medium.md`)
- LinkedIn feed post (`4-linkedin/post.md`)
- Twitter/X thread (`5-twitter/thread.md`)
- Website post files (`2-website/post-meta.md` + `2-website/post-body.md`)
- Optionally: LinkedIn carousel and Twitter image thread

At the end, Claude outputs a publishing checklist, updates `INDEX.md` status to "Content Drafted", writes the title back to `meta.md`, and appends sequel seeds to `sequel-seeds.md`.

---

## File and Folder Reference

**`AI-CONTEXT.md`** is the single source of truth for all strategic and structural knowledge. Both Claude Code and Gemini App are instructed to read this file at the start of every session. Update it when you want to change the content strategy, funnel architecture, tag ordering logic, or any convention that applies to both AIs.

**`pillars.md`** contains the canonical 2-pillar definitions used by all slash commands. Update this file (not AI-CONTEXT.md) when the content strategy changes — all commands automatically use the updated definitions in the next session.

**`website-schema.json`** defines the Sanity CMS field schema. Update this file when the Sanity schema changes — commands read it directly rather than inspecting existing article files.

**`CLAUDE.md`** contains Claude Code's role-specific instructions. Update it only when changing something specific to how Claude behaves.

**`GEMINI.md`** contains Gemini's role-specific instructions. Update it when changing how Gemini should structure its research output.

**`categories.md`** is the living registry of all approved content categories. Never manually add a category to a content file that isn't in this registry — let Claude propose it at the checkpoint.

**`README.md`** is this file. It is not read by the AI tools.

**`career/articles/INDEX.md`** is the article tracker table. It lists every article with its index number, slug, title, pillar, category, dates, and status. Claude Code reads this file to determine the next index number when creating a new article folder and updates it at the start and end of each pipeline run.

**`career/articles/sequel-seeds.md`** is the lightweight sequel opportunity index. It is updated by `/draft-content` after each article is drafted. `/draft-calendar` reads this file to surface sequel ideas without opening individual research files.

**`career/articles/NNN-SLUG/`** is where all files for a given article live. Each article has its own folder named with a 3-digit index prefix and SLUG. Inside:

- `meta.md` — slug, title, created date, intended publish date, published date, pillar, category, tags, flags
- `1-research/prompts.md` — the two Gemini research prompts generated by `/draft-research`
- `1-research/research-raw.md` — raw Gemini Deep Research output (**read-restricted**: Claude will not open this without your explicit instruction)
- `1-research/research.md` — structured, summarised research + Research Utilisation Summary + Decisions Log
- `2-website/post-meta.md` — Sanity CMS metadata (title, seoTitle, category, tags, timeToRead, image prompt)
- `2-website/post-body.md` — full article Markdown body (same content as `medium.md` at time of generation)
- `3-medium/medium.md` — long-form article draft for Medium and LinkedIn Newsletter
- `4-linkedin/post.md` — LinkedIn feed post
- `4-linkedin/carousel-script.md` — carousel slide script (if produced)
- `4-linkedin/carousel-post.md` — accompanying carousel LinkedIn post (if produced)
- `5-twitter/thread.md` — Twitter/X thread
- `5-twitter/imagethread-script.md` — image thread script (if produced)
- `5-twitter/image-prompts.md` — AI image generation prompts (if produced)

**`career/research/`** contains standalone research documents not tied to a specific article. Leave this folder as is.

**`.claude/commands/`** contains the nine slash command definition files.

---

## The Nine Slash Commands

**`/draft-research <topic>`** — Phase 1 of the pipeline. Assigns next index number, classifies the topic, confirms the category, generates research prompts inside the new article folder, outputs the Gemini handoff block.

**`/draft-content <slug>`** — Phase 2 of the pipeline. Takes a bare SLUG (case-insensitive). Requires `1-research/research.md` to exist. Produces all content formats, updates INDEX.md, meta.md, and sequel-seeds.md on completion. Append "full draft" to skip the outline checkpoint. Append "carousel" and/or "imagethread" to pre-confirm those optional outputs.

**`/draft-calendar`** — Generates or updates your rolling 4-week content calendar. Reads `INDEX.md` and `sequel-seeds.md` only (efficient — no research files opened). Respects `calendarAI` setting in `AI-CONTEXT.md`.

**`/draft-medium <slug>`** — Standalone long-form article only. Includes pre-validation check, content volume assessment, and Research Utilisation Summary.

**`/draft-linkedin <slug>`** — Standalone LinkedIn feed post only. Reuses any existing `research.md` or `medium.md` for the same topic rather than running new research.

**`/draft-twitter <slug>`** — Standalone Twitter/X thread only. Same reuse behaviour.

**`/draft-website <slug>`** — Standalone website post generator. Reads `website-schema.json` for the canonical field list. Produces `2-website/post-meta.md` and `2-website/post-body.md`.

**`/draft-carousel <slug>`** — Standalone LinkedIn carousel. Produces the slide script, attempts to render a PDF via Python, and produces the accompanying post text. If PDF rendering fails, the slide script is saved ready for manual import into Canva.

**`/draft-imagethread <slug>`** — Standalone Twitter image thread. Produces tweet captions and AI image generation prompts. Images are generated externally using those prompts.

---

## How to Run the Typical Publishing Workflow

1. Open Claude Code in this workspace.
2. Run `/draft-research <your topic or angle>` and follow the prompts.
3. Complete the Gemini steps from the handoff block (Deep Research, then Summarization).
4. Save the outputs to `career/articles/NNN-SLUG/1-research/research-raw.md` and `research.md`.
5. Run `/draft-content <slug>`. Respond to the checkpoints (tags, article length, outline, visual style, optional formats).
6. Follow the publishing checklist Claude outputs at the end: website first, then Medium, then LinkedIn Newsletter, then LinkedIn feed post, then carousel if produced, then Twitter thread, then image thread if produced.

---

## How to Upload to Sanity CMS

After `/draft-content` or `/draft-website` runs, assemble the website post JSON manually:
1. Open `2-website/post-meta.md` — copy all frontmatter fields into a JSON object
2. Open `2-website/post-body.md` — use its contents as the `body` field
3. Validate the assembled JSON against `website-schema.json`
4. Rename to `[created date from meta.md]_SLUG.json` before uploading

---

## How to Update AI-CONTEXT.md

Edit directly in your text editor. Changes take effect the next time you open a new Claude Code session — there is no sync command to run.

---

## How to Update the Content Strategy (Pillars)

Edit `pillars.md` directly. All slash commands read this file at the start of every pillar classification step, so changes take effect immediately in the next session. Also update the human-readable description in `AI-CONTEXT.md` for reference.

---

## How to Update the Sanity CMS Schema

Edit `website-schema.json` directly. Add, remove, or rename fields as needed. Commands read this file rather than inspecting existing articles, so all future website posts will automatically conform.

---

## How to Add a New Slash Command

Create a new `.md` file in `.claude/commands/` following the naming pattern `draft-<commandname>.md`. Write the steps inside using the same structure as the existing commands. Add the new command to the Slash Commands section of `CLAUDE.md` with a one-line description. Update `AI-CONTEXT.md` only if the new command introduces a structural convention that applies workspace-wide.

---

## How to Add a New Content Category

Do not add categories manually. Run any draft command for a piece that requires a new category, and Claude will propose one and pause for your approval before adding it to `categories.md`. This ensures the category is always logged with the correct date and article association.

---

## Troubleshooting

**Claude ignores the persona or tone:** Most likely it did not read `AI-CONTEXT.md` at session start. Open a new session and ask: "Please read AI-CONTEXT.md and confirm you understand the workspace."

**Claude classifies content into the wrong pillar:** Check that `pillars.md` reflects the current 2-pillar strategy. If the file is correct, the command may have cached an old version — open a new session.

**Gemini returns unstructured output:** Check that the research prompt in `career/articles/NNN-SLUG/1-research/prompts.md` explicitly specifies the expected section headings.

**A carousel PDF fails to render:** The slide script is saved as a fallback at `career/articles/NNN-SLUG/4-linkedin/carousel-script.md`. Copy the content into Canva or Adobe Express to render manually.

**Sanity CMS upload fails schema validation:** Check the assembled JSON against `website-schema.json`. Common causes: a missing field, wrong data type, or trailing comma. Remember to rename the file to `DATE_SLUG.json` before uploading.

**`/draft-content` can't find the article:** Make sure you're passing a SLUG, not a topic phrase. Check that the slug appears in `INDEX.md`. The command accepts any case — `Monetask-18-Months-Never-Shipped` will resolve correctly.
