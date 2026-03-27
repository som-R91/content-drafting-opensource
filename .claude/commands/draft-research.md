# Draft Research Prompts

You are generating the research prompts for a new article in Somaditya Roy's content pipeline. This command handles everything up to research — it does not draft any content. The output is two structured prompts that Somaditya will use manually in Gemini App's Deep Research mode before running `/draft-content`.

The topic or angle is: $ARGUMENTS

Read this entire command before beginning. The sequence is intentional — do not reorder steps.

---

## Step 0 — Sequel Seed Check

Before doing anything else, read `career/articles/sequel-seeds.md` and check whether the requested topic matches any existing sequel seed entry. Use fuzzy matching — the topic doesn't need to be an exact string match, just a clear thematic overlap.

**If a match is found**, surface it to Somaditya:

```
SEQUEL SEED DETECTED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
This topic matches an existing sequel seed:
  "[seed title]"
  Source: [path to research.md in the original article folder]

Options:
  A — Reuse existing research (skip Gemini step, go straight to /draft-content)
  B — Run fresh research for this angle
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for Somaditya's answer before proceeding.

**If Option A (reuse existing research):**
1. Proceed through Steps 1–6 as normal to create the new folder, meta.md, and INDEX.md row.
2. After creating `career/articles/FOLDER/1-research/`, copy `research.md` from the source article's `1-research/` folder into the new article's `1-research/` folder. Do **not** copy `research-raw.md` — it is read-restricted and very large.
3. Remove the matched entry from `career/articles/sequel-seeds.md` to prevent duplication. (The entry would otherwise reappear after `/draft-content` runs on the new article and appends its own sequel seeds.)
4. Skip the prompt generation steps (Steps 4's PROMPT 1 and PROMPT 2 content) and replace the handoff block in Step 7 with:

```
RESEARCH ALREADY AVAILABLE — NO GEMINI STEP NEEDED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Research copied from:
  [source path]
Saved to:
  career/articles/FOLDER/1-research/research.md

Continue with:
  /draft-content SLUG
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**If Option B (fresh research) or no match found:** proceed with the standard flow below.

---

## Step 1 — Session Variables

Establish the values that identify this article throughout the pipeline:

1. **SLUG**: a kebab-case topic slug of 5–6 words that precisely describes this article's angle (not just the broad topic — e.g., `retention-cohort-analysis-b2b-saas`, not just `retention`)
2. **DATE**: today's date in YYYY-MM-DD format (stored in meta.md, not used in folder or file names)

Read `career/articles/INDEX.md` to determine the next index number: NNN = (last # in the table) + 1, zero-padded to 3 digits. Set **FOLDER = NNN-SLUG** (e.g., `006-retention-cohort-analysis-b2b-saas`).

Check whether "full draft", "carousel", or "imagethread" appears in $ARGUMENTS and note these flags — they will be passed to `/draft-content` when that command runs.

---

## Step 2 — Pillar Classification

Read `pillars.md` from the workspace root for the canonical pillar definitions. Classify the topic into exactly one of the two pillars defined there. State your choice and a one-sentence justification before proceeding. If the topic is genuinely ambiguous between two pillars, present both options and **pause to ask Somaditya which framing to pursue.** Wait for the answer.

---

## Step 3 — Category Assignment

Read `categories.md` from the workspace root. Propose one category from the existing Active Categories list, showing Somaditya the full current list alongside your proposal so he can confirm or redirect.

If no existing category fits well, propose a new one (noun phrase, specific enough to be a meaningful filter label, broad enough for multiple future articles to share it, grammatically consistent with existing categories). **Pause for explicit approval before continuing.** Once approved, update `categories.md`: add to Active Categories and log in the Category Addition Log table with today's date and this article's working title.

**Checkpoint — wait for category confirmation before moving to Step 4.**

---

## Step 4 — Create Article Folder and Research Prompts

1. Create `career/articles/FOLDER/` if it does not already exist.
2. Create `career/articles/FOLDER/1-research/`.
3. Generate two structured research prompts (see below).
4. Save both prompts to `career/articles/FOLDER/1-research/prompts.md`.

### PROMPT 1 — DEEP RESEARCH
*(For Gemini App → Deep Research mode. This is the exhaustive first pass.)*

Write a prompt that instructs Gemini to:
- Search exhaustively across academic sources, practitioner blogs, conference talks, case studies, and industry reports
- Return all statistics with full source URLs and publication dates
- Return all frameworks with creator/origin, year introduced, and description of each component
- Return all case studies with specific measurable outcomes and the year they occurred
- Include contrarian positions from named practitioners (with their name, title, and where they stated this)
- Include direct quotes where available, attributed to named individuals
- Flag conflicting data points explicitly — present both versions side by side
- Note known criticisms or limitations of the mainstream frameworks
- Explicitly state when a claim is an approximation or cannot be fully sourced
- **Do not summarise. Aim for volume and accuracy over brevity.**

The target topic is the SLUG/article angle established in Steps 1–3. Include the pillar and category in the prompt for context.

### PROMPT 2 — SUMMARIZATION
*(For a second Gemini conversation. Somaditya will paste the full PROMPT 1 output at the end of this prompt.)*

Write a prompt that instructs Gemini to:
- Structure the raw research into exactly these sections, preserving all citations:
  - **LANDSCAPE** — the current state of practice and why it falls short for senior practitioners
  - **DATA** — 5–6 specific statistics or research findings, each with source and date
  - **FRAMEWORKS** — 2–3 named frameworks or mental models with creator/origin and component descriptions
  - **CASE STUDIES** — 2–3 real-world examples with specific measurable outcomes and year
  - **CONTRARIAN ANGLE** — one well-reasoned position challenging the mainstream view, attributed to a named practitioner where possible
  - **PRACTITIONER MISTAKES** — top 3 mistakes mid-to-senior PMs make on this topic, each as a concrete scenario
  - **HOOK IDEAS** — 3 candidate hook sentences for a LinkedIn post, each presenting a different angle
  - **CAROUSEL HOOK** — one striking stat or counterintuitive claim powerful enough to stop a senior PM from swiping past a carousel cover slide
  - **SEQUEL SEEDS** — 2–3 related sub-topics that could each sustain their own full article
- Flag any conflicting data points (present both versions, do not resolve them)
- Invent nothing not present in the source material
- Preserve all source citations in every section

---

## Step 5 — Create meta.md

Create `career/articles/FOLDER/meta.md` with the following content:

```
---
slug: SLUG
title:
created: DATE
intended-publish:
published:
pillar: [pillar confirmed in Step 2]
category: [category confirmed in Step 3]
tags:
flags: [any flags from $ARGUMENTS, or "none"]
---
```

---

## Step 6 — Update INDEX.md

Add a new row to `career/articles/INDEX.md` for this article:

```
| NNN | SLUG | — | [pillar] | [category] | DATE | — | — | Folder Created | |
```

Status is `Folder Created` at this stage.

---

## Step 7 — Handoff Block

End with this formatted handoff block:

```
RESEARCH STEP — ACTION REQUIRED BEFORE CONTINUING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Prompts saved to:
  career/articles/FOLDER/1-research/prompts.md

Article folder created:
  career/articles/FOLDER/

Step 1 — Deep Research
  Tool:     Gemini App → Deep Research mode
  Prompt:   PROMPT 1 (full text in prompts file above)
  Save output to:
  career/articles/FOLDER/1-research/research-raw.md

Step 2 — Summarization
  Tool:     Gemini App (new conversation)
  Prompt:   PROMPT 2 (full text in prompts file above)
            + paste the complete research-raw.md output at the end
  Save output to:
  career/articles/FOLDER/1-research/research.md

⚠  Claude will not read research-raw.md unless you explicitly ask.

When both files are saved, continue with:
  /draft-content SLUG
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```
