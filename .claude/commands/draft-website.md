# Draft Website Post (Sanity CMS)

You are creating the website post files for Somaditya Roy's personal website. This produces two Markdown files — `post-meta.md` (structured metadata) and `post-body.md` (article body) — inside the article's `2-website/` folder. At export time, these are assembled into a Sanity CMS-compatible JSON file.

The topic or project to feature is: $ARGUMENTS

Before starting, normalize $ARGUMENTS to lowercase and derive the topic slug (kebab-case, max 5–6 words, matching the slug used for the related article if one exists). Read `career/articles/INDEX.md` to find the matching `NNN-SLUG` folder (case-insensitive). Store this as **FOLDER**.

If a long-form article draft already exists at `career/articles/FOLDER/3-medium/medium.md`, use its content for `post-body.md` directly. If research exists at `career/articles/FOLDER/1-research/research.md`, load it and skip Step 4.

---

## Step 1 — Load Schema

Read `website-schema.json` from the workspace root. This is the canonical list of fields required for `post-meta.md`. Do not inspect any existing article's `post-meta.md` to infer the schema — the JSON file is the authority. Note every field name, data type description, and any constraints before proceeding.

---

## Step 2 — Pillar Classification & Portfolio Positioning

Read `pillars.md` from the workspace root for the canonical pillar definitions. Classify the piece into exactly one of the two pillars defined there.

Then state explicitly: what specific capability claim does this piece make about Somaditya, and what evidence does it present to support that claim? Website pieces are evidence artefacts, not articles.

---

## Step 3 — Category Assignment

Read `categories.md` from the workspace root. Propose one category from the existing Active Categories list. If no existing category fits well, propose a new one and **pause for Somaditya's explicit approval before continuing.** Once approved, update `categories.md` — add to Active Categories and log in the Category Addition Log table with today's date.

---

## Step 4 — Tag Generation

Generate 8–10 tags ordered strictly from most to least relevant using the following priority logic:

The first tag is the piece's primary topic keyword — the most precise single term describing what this piece is fundamentally about, written as a recruiter searching Google for a "senior PM portfolio [topic]" would phrase it. Tags two and three are the methodology or framework demonstrated. Tags four through six are supporting domain concepts directly addressed in the body. Remaining tags are adjacent topics a reader of this piece would also care about.

All tags: lowercase, hyphens for multi-word terms, real practitioner vocabulary only.

---

## Step 5 — Research (skip if article draft or research file already exists)

If no research file exists at `career/articles/FOLDER/1-research/research.md` and no article draft exists at `career/articles/FOLDER/3-medium/medium.md`, **stop here** and output:

"No research found for this topic. Run `/draft-research <topic>` first, complete the Gemini Deep Research and Summarization steps, save the output to `career/articles/FOLDER/1-research/research.md`, then return to this command."

Do not proceed until research is available.

---

## Step 6 — Generate the Image Prompt

Generate a detailed `mainImagePromptToGenerateImageUsingAI` prompt specific to this piece's theme — subject matter, mood, colour palette, composition. Do not reuse prompts from other articles.

**Pause and ask:** "Which visual style — **lifelike**, **photo-realistic**, **illustration**, or **Ghibli**?" Append the chosen style as the final instruction.

---

## Step 7 — Generate the Body

If a `career/articles/FOLDER/3-medium/medium.md` exists, use its full Markdown content as the body. If not, write a structured case study of 400–700 words covering: business context and problem, approach and methodology with specific tools and frameworks named, outcome with metrics wherever possible, and one extracted principle or learning. Write in Somaditya's authoritative first-person voice.

Then ask yourself: would a senior hiring manager at a B2B SaaS company read this and want to reach out to Somaditya? If not, identify the weakest section and strengthen it before saving.

---

## Step 8 — Validate and Save

Using the fields from `website-schema.json` (Step 1), generate the following files:

**`career/articles/FOLDER/2-website/post-meta.md`:**

```markdown
---
title: [specific, outcome-oriented headline]
seoTitle: [rewritten for search intent with 1–2 primary keywords]
category: [approved category — must match categories.md exactly]
tags:
  - [tag1]
  - [tag2]
  ...
timeToRead: [body word count ÷ 200, rounded]
---

## Cover Image Prompt

[mainImagePromptToGenerateImageUsingAI — full paragraph with visual style appended]
```

**`career/articles/FOLDER/2-website/post-body.md`:**

Full article or case study in Markdown.

Verify before saving: every required field from `website-schema.json` is present in `post-meta.md`, no extra fields were added, and all values are correctly typed.

Output the complete `post-meta.md` and `post-body.md` contents to the terminal.

Remind Somaditya: "To upload to Sanity CMS, assemble these two files into a JSON object matching the schema in `website-schema.json`, using the `post-meta.md` frontmatter fields and the `post-body.md` content as the `body` field. Rename the assembled JSON to `[created date from meta.md]_SLUG.json` before uploading."
