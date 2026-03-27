# Draft Content From Research

You are picking up the content pipeline after Somaditya has completed the manual Gemini research steps. This command takes a SLUG (not a topic) and drafts all content formats from the research already saved in the article folder.

The SLUG is: $ARGUMENTS

Read this entire command before beginning. If $ARGUMENTS is empty or is clearly a topic phrase rather than a SLUG, stop and say: "This command takes a SLUG, not a topic. Run `/draft-research <topic>` first, then return here with the SLUG."

---

## Step 1 — Resolve SLUG and Load Research

Normalize $ARGUMENTS to lowercase. Read `career/articles/INDEX.md` to find the matching `NNN-SLUG` folder. Store this as **FOLDER**. Case-insensitive matching: `Monetask-18-Months-Never-Shipped` resolves to `002-monetask-18-months-never-shipped`.

If no match is found: stop and output — "SLUG not found in INDEX.md. Check the slug or run `/draft-research <topic>` first."

Check that `career/articles/FOLDER/1-research/research.md` exists and is non-empty.

- If the file is missing: stop and output — "research.md not found at career/articles/FOLDER/1-research/research.md. Complete the Gemini research steps described in the handoff block from `/draft-research`, then save the output to that path."
- If the file exists but appears truncated or suspiciously short (under 500 words): flag this to Somaditya and ask whether to proceed or re-run the summarization step.

Read `career/articles/FOLDER/1-research/research.md` in full. Do not read `research-raw.md` — that file is read-restricted.

---

## Step 2 — Load Session Context

Read `career/articles/FOLDER/1-research/prompts.md` to recover:
- The content pillar assigned in `/draft-research`
- The category assigned and confirmed
- Any flags set (carousel, imagethread, full draft)

If the prompts file is missing, ask Somaditya to confirm the pillar, category, and any flags before proceeding.

---

## Step 3 — Tag Generation

Using the research, generate 8–10 tags ordered from most to least relevant:

The first tag is the article's primary topic keyword — the single most precise term a recruiter or senior PM would type into Google to find this piece. Tags two and three are the primary methodology or framework featured. Tags four through six are supporting domain concepts directly addressed in the article. Remaining tags are adjacent context topics a reader of this piece would also care about.

All tags: lowercase, hyphens for multi-word terms (e.g., `north-star-metric`, `churn-cohort-analysis`), real practitioner vocabulary only. This ordering matters: Sanity CMS, LinkedIn, Medium, and search engine crawlers weight earlier array items more heavily.

**Checkpoint — present the proposed tag list and ask:** "Any tags to add, remove, or reorder before I start drafting?" Wait for feedback, then finalise the list. Write the finalised tags back to `career/articles/FOLDER/meta.md` in the `tags:` field.

---

## Step 4 — Article Length Assessment

Before building the outline, assess the research for content volume. Count the major ideas, framework components, case studies, and SEQUEL SEEDS in the research. Then present:

```
CONTENT VOLUME ASSESSMENT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Major ideas available: [N]
Framework components: [N]
Case studies: [N]
Estimated word count at full coverage: ~[N] words

Recommendation: [one of the following]
  Option A — Single article, 1,200–1,800 words (6–9 min read).
              Covers: [specific sections].
              Saves for sequels: [specific sections].
  Option B — Single long-form piece, 2,000–2,500 words (10–12 min read).
              Covers: [specific sections].
  Option C — Part 1 now + Part 2 later.
              Part 1 covers: [specific sections].
              Part 2 would cover: [specific sections — saved in research file].
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Checkpoint — ask:** "Which option would you like?" Wait for the answer before building the outline. Note: Option A is recommended because 1,200–1,800 words is the engagement sweet spot for Medium and LinkedIn Newsletter. The research file preserves all unused material for future sessions — nothing is lost by choosing Option A.

---

## Step 5 — Long-Form Article

Using the research from Step 1 and the length decision from Step 4, build the outline following this structure:

Opening Hook (no heading): 2–3 paragraphs. Specific scenario, data point, or moment from Somaditya's experience. Close with a clear promise of what the article teaches.

Section 1 — The Problem Most PMs Miss: Core misconception using LANDSCAPE and PRACTITIONER MISTAKES from research.

Section 2 — The Framework (name it): Central reusable framework with a memorable name. Named frameworks get saved, cited, and searched. Use FRAMEWORKS and CASE STUDIES from research.

Section 3 — Real-World Application: Concrete examples from CASE STUDIES. Specificity builds credibility.

Section 4 — Common Mistakes & How to Avoid Them: Top 2–3 PRACTITIONER MISTAKES each paired with a concrete fix.

Closing + CTA: One actionable takeaway. CTA driving to Somaditya's website or related content.

**If "full draft" was NOT in the flags (Step 2):** pause, present the outline, and wait for approval before writing prose.
**If "full draft" WAS in the flags:** proceed directly to prose.

**If Somaditya rejects the outline:** ask for the specific section(s) to revise rather than restarting the entire outline. Revise only the flagged sections, re-present the outline, and wait for re-approval before drafting prose.

Write the full article in Markdown. Tone: authoritative, pragmatic, metrics-grounded, from lived experience. No hedging. No generic openers. Use `##` headers. Use `**bold**` sparingly for framework terms and key data points only.

Save as `career/articles/FOLDER/3-medium/medium.md`.

**Checkpoint — present the article and ask:** "Any edits to the long-form article before I generate the short-form content?" Wait for approval or "proceed" before continuing.

---

## Step 6 — Research Utilisation Summary

Append the following summary to `career/articles/FOLDER/1-research/research.md`:

```
## Research Utilisation Summary — Added [DATE]

Used in the [DATE] article:
  [list specific data points, frameworks, case studies used]

Available for sequels:
  [list unused SEQUEL SEEDS and unused research sections]

Suggested next article: [one-sentence pitch for the most logical sequel]
```

---

## Step 7 — Image Prompt & Visual Style

Generate a `mainImagePromptToGenerateImageUsingAI` prompt specific to this article's theme — subject matter, mood, colour palette, composition. Do not reuse prompts from previous articles.

**Checkpoint — pause and ask:** "Which visual style for this cover image?"

Present the options:
- **Lifelike** — hyper-realistic rendering, tactile and physical
- **Photo-realistic** — as if shot by a professional photographer
- **Illustration** — clean vector or editorial illustration style
- **Ghibli** — Studio Ghibli animation aesthetic, warm and painterly

Wait for the choice, then append the style as the final sentence of the image prompt.

---

## Step 8 — Optional Agents: Carousel and Image Thread

**Checkpoint — ask Somaditya two questions before proceeding (skip if pre-confirmed in flags from Step 2):**

"Would you like me to also generate a **LinkedIn carousel** for this topic? This is a PDF with 8–12 swipeable slides — the highest-engagement format on LinkedIn with a 6.60% average engagement rate. (yes / no)"

"Would you like me to also generate a **Twitter/X image thread** for this topic? This is a series of 4–7 tweets each with a designed image card. (yes / no)"

Wait for both answers before proceeding.

**If LinkedIn carousel is confirmed:** Execute the full `draft-carousel` logic for this topic, drawing from the research already saved in `career/articles/FOLDER/1-research/research.md`. Do not re-run research. Save outputs to:
- `career/articles/FOLDER/4-linkedin/carousel-script.md`
- `career/articles/FOLDER/4-linkedin/carousel-post.md`

Note that this carousel format uses the CAROUSEL HOOK from the research (Step 1). If a narrative structure hasn't been selected yet, pause and ask Somaditya to choose one: Problem → Solution, Step-by-Step Guide, Before → After, Myth vs. Fact, or Data Story.

**If Twitter image thread is confirmed:** Execute the full `draft-imagethread` logic, drawing from the same research. Do not re-run research. Pause to ask the visual style question (bold typographic, data visualisation, illustration, or Ghibli). Save outputs to:
- `career/articles/FOLDER/5-twitter/imagethread-script.md`
- `career/articles/FOLDER/5-twitter/image-prompts.md`

---

## Step 9 — LinkedIn Feed Post

Using the long-form article from Step 5 and the HOOK IDEAS from the research, write a LinkedIn post of 150–300 words using the Hook → Rehook → Body → Value Close → CTA structure.

Hook (lines 1–2): Choose the strongest hook from research HOOK IDEAS, or write a better one. First two lines stand alone as a reason to expand. Never open with "I" or a question.

Body: Single-sentence paragraphs with line breaks. `**Bold**` for framework terms. Maximum 2 emojis as visual anchors. Every sentence earns its place.

CTA: Drive to the article specifically. One or two lines, no hedging.

No bullet lists.

**Hashtags:** Add 3–5 hashtags at the very end of the post, on their own line, after the CTA. Use this mix: 1–2 broad reach tags (e.g. `#productmanagement`, `#product`, `#startup`) + 1–2 niche tags specific to the post's core topic + 1 pillar-specific recurring tag (`#BuildingCatalyst` for Pillar 2, `#ShippingWithoutTheTitle` for Pillar 1).

Save as `career/articles/FOLDER/4-linkedin/post.md`.

---

## Step 10 — Twitter/X Thread

Using the same research and article, write a thread of 6–10 tweets. Extract the three most scroll-stopping data points and the most memorable analogy from the research.

Tweet 1: Hook. 280 characters maximum. Most counterintuitive finding or sharpest stat. Implicit promise.

Tweets 2–N: One idea per tweet. Numbered ("2/", "3/", etc.). Concrete, specific, quotable.

Final tweet: CTA to owned asset. Two lines maximum. Add 2–3 hashtags at the end of this final tweet only — 1 broad tag (e.g. `#ProductManagement` or `#BuildInPublic`) + 1–2 topic-specific tags.

Save as `career/articles/FOLDER/5-twitter/thread.md`.

---

## Step 11 — Website Post Files

Read `website-schema.json` from the workspace root to confirm the canonical field list. Do not inspect any existing article's `post-meta.md` — the schema file is the authority.

Pull every field from what has already been generated — do not regenerate content:
- `title` from the article headline (outcome-oriented)
- `subtitle` a specific, outcome-oriented subtitle that aligns with the headline or key takeaway
- `seoTitle` rewritten for search intent (≤60 chars, primary keyword first)
- `seoDescription` 150–160 character SERP snippet, compelling and keyword-rich
- `seoKeywords` 8–10 search-intent terms ordered most to least relevant (what people type into Google)
- `category` the approved value from Step 2 (must match `categories.md` exactly)
- `tags` the ordered practitioner vocabulary array from Step 3
- `timeToRead` body word count ÷ 200, rounded
- `mainImagePromptToGenerateImageUsingAI` the finalised prompt with style from Step 7
- `mainImageCaption` a short 1-line phrase or sentence that serves as the main image caption

Save `career/articles/FOLDER/2-website/post-meta.md` in this format:

```markdown
---
title: [title]
subtitle: [subtitle]
seoTitle: [seoTitle]
seoDescription: [seoDescription]
seoKeywords:
  - [keyword1]
  - [keyword2]
category: [category]
tags:
  - [tag1]
  - [tag2]
timeToRead: [N]
mainImageCaption: [mainImageCaption]
---

## Cover Image Prompt

[mainImagePromptToGenerateImageUsingAI — full paragraph with style appended]
```

Save `career/articles/FOLDER/2-website/post-body.md` with the full article Markdown from Step 5 (identical content to `3-medium/medium.md`).

---

## Step 12 — Publishing Checklist + Updates

Output the following publishing checklist:

```
PUBLISHING CHECKLIST — [Article Title]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Folder:           career/articles/FOLDER/
Category:         [approved category]
Pillar:           [pillar name]
Tags (ordered):   [tag 1], [tag 2], [tag 3], ...
Read time:        [N] min

FILES GENERATED
  ✓ 1-research/research.md    → preserved research + utilisation summary
  ✓ 3-medium/medium.md        → publish to Medium + LinkedIn Newsletter
  ✓ 4-linkedin/post.md        → post to LinkedIn feed
  ✓ 5-twitter/thread.md       → post to Twitter/X
  ✓ 2-website/post-meta.md    → Sanity CMS metadata
  ✓ 2-website/post-body.md    → Sanity CMS article body
  [if carousel: ✓ 4-linkedin/carousel-script.md + carousel-post.md]
  [if imagethread: ✓ 5-twitter/imagethread-script.md + image-prompts.md]

MANUAL STEPS REMAINING
  □ Generate cover image using the prompt in 2-website/post-meta.md
     Style selected: [style]
  □ Generate OpenGraph image at your OG image tool
     Title for OG (check length): [article title]
     [if title > 60 characters: ⚠ LONG TITLE — suggested short version: [shortened title]]
     Category shown on OG: [approved category]
  □ Assemble Sanity CMS JSON from post-meta.md + post-body.md, rename to
     [created date from meta.md]_SLUG.json before uploading
  [if carousel: □ Review carousel PDF — if rendering failed, use carousel-script.md in Canva]
  [if imagethread: □ Generate images using prompts in image-prompts.md, attach to tweets]
  □ Review and lightly edit all files as needed
  □ Publish in this order:
     1. Website (establishes canonical URL)
     2. Medium
     3. LinkedIn Newsletter
     4. LinkedIn feed post (now has a link to reference)
     [if carousel: 4b. LinkedIn carousel post]
     5. Twitter/X thread
     [if imagethread: 5b. Twitter/X image thread]

SEQUEL OPPORTUNITIES
  [list the SEQUEL SEEDS from the research, as one-line pitches]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Then perform these three updates:

**1. Update INDEX.md:** Change the status for this article's row to `Content Drafted`.

**2. Update meta.md:** Set the `title:` field to the article title established in Step 5.

**3. Update sequel-seeds.md:** Append the SEQUEL SEEDS from the Research Utilisation Summary to `career/articles/sequel-seeds.md` in this format:
```
## Sequels from FOLDER (added DATE)
- [one-line pitch for sequel] — research available at career/articles/FOLDER/1-research/research.md
- [one-line pitch for sequel] — research available at career/articles/FOLDER/1-research/research.md
```

Then append a `DECISIONS LOG` block to `career/articles/FOLDER/1-research/research.md`:

```
## Decisions Log — [DATE]

| Decision Point | Choice Made | Rationale |
|---|---|---|
| Pillar | [Pillar 1/2] | [one-line justification] |
| Category | [category name] | [new or existing] |
| Article length | [Option A/B/C] | [recommendation followed or overridden] |
| Outline approved | [yes / revised] | [what changed, if anything] |
| Visual style | [style chosen] | — |
| Carousel | [yes / no] | — |
| Image thread | [yes / no] | — |
| Carousel narrative | [structure chosen or N/A] | [one-line rationale or N/A] |
```
