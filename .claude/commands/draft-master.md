# Master Content Pipeline

You are orchestrating the full end-to-end content creation pipeline for [YOUR NAME], as defined in `AI-CONTEXT.md`. This command coordinates all content formats for a single topic in a deliberate sequence, shares research and drafts across formats to eliminate redundant work, and pauses at the right moments to collect decisions before proceeding.

Read `AI-CONTEXT.md` before beginning if you have not already done so this session. The persona, pillars, tone, and all workspace conventions live there. Read this entire command before beginning. The sequence is intentional — do not reorder steps.

The topic or angle is: $ARGUMENTS

---

## Step 0 — Initialise Session Variables

Before doing anything else, establish the two values that prefix every filename this session produces:

1. **DATE**: today's date in YYYY-MM-DD format
2. **SLUG**: a kebab-case topic slug of 5–6 words that precisely describes this article's angle (not just the broad topic — e.g., `retention-cohort-analysis-b2b-saas`, not just `retention`)

Check whether "full draft" appears in $ARGUMENTS. If it does, note that the outline approval checkpoint in Step 6 will be skipped and the pipeline will proceed end-to-end. All other checkpoints still apply.

Check whether "carousel" or "imagethread" appears in $ARGUMENTS. If either or both appear, note that the corresponding optional agents in Step 9 will be pre-confirmed and will not require a separate checkpoint pause.

---

## Step 1 — Pillar Classification

Classify the topic into exactly one of the three content pillars defined in `AI-CONTEXT.md` under **The Rule of Three Content Pillars**. State your choice and a one-sentence justification before proceeding. If the topic is genuinely ambiguous between two pillars, present both options and **pause to ask which framing to pursue.** Wait for the answer.

---

## Step 2 — Category Assignment

Read `categories.md` from the workspace root. Propose one category from the existing Active Categories list, showing the full current list alongside your proposal so it can be confirmed or redirected.

If no existing category fits well, propose a new one (noun phrase, specific enough to be a meaningful filter label, broad enough for multiple future articles to share it, grammatically consistent with existing categories). **Pause for explicit approval before continuing.** Once approved, update `categories.md`: add to Active Categories and log in the Category Addition Log table with today's date and this article's working title.

**Checkpoint — wait for category confirmation before moving to Step 3.**

---

## Step 3 — Deep Research via Gemini

First check: does a research file already exist at `career/research/DATE_SLUG-research.md` or a recent file with the same slug? If so, load it and skip the Gemini call — note that existing research is being used.

If no research exists, run the following comprehensive research call. This output serves all formats (article, post, thread, carousel, image thread) — running it once here means no subsequent command needs to call Gemini again for this topic.

```bash
gemini -p "You are a research assistant for a [YOUR ROLE/PROFESSION] creating a full content package including a long-form article, LinkedIn carousel, LinkedIn post, and Twitter thread. Conduct thorough research on the following topic and return structured findings in these exact labelled sections — LANDSCAPE: the current state of practice and why it falls short for senior practitioners; DATA: 5-6 specific statistics or research findings with sources; FRAMEWORKS: 2-3 named frameworks or mental models including name, origin, and component descriptions; CASE STUDIES: 2-3 real-world company examples with specific measurable outcomes; CONTRARIAN ANGLE: one well-reasoned position challenging the mainstream view; PRACTITIONER MISTAKES: the top 3 mistakes mid-to-senior practitioners make on this topic, each as a concrete scenario; HOOK IDEAS: 3 candidate hook sentences for a LinkedIn post — each presenting a different angle; CAROUSEL HOOK: one striking stat or counterintuitive claim powerful enough to stop a senior practitioner from swiping past a carousel cover slide; SEQUEL SEEDS: 2-3 related sub-topics that could each sustain their own full article. Topic: $ARGUMENTS"
```

> **Setup note:** Replace `[YOUR ROLE/PROFESSION]` in the prompt above with your actual role — for example, "senior B2B SaaS Product Manager", "Staff Software Engineer", or "Growth Marketing Director". The more specific the role description, the more targeted Gemini's research will be.

Save the complete, untruncated output to `career/research/DATE_SLUG-research.md` immediately. Confirm the file path and word count before proceeding.

---

## Step 4 — Tag Generation

Using the research output, generate 8–10 tags ordered from most to least relevant:

The first tag is the article's primary topic keyword — the single most precise term a recruiter or practitioner in the target field would type into Google to find this piece. Tags two and three are the primary methodology or framework featured. Tags four through six are supporting domain concepts directly addressed in the article. Remaining tags are adjacent topics a reader of this piece would also care about.

All tags: lowercase, hyphens for multi-word terms (e.g., `north-star-metric`, `churn-cohort-analysis`), real practitioner vocabulary only. This ordering matters: LinkedIn, Medium, the CMS, and search engine crawlers weight earlier array items more heavily. Precise domain terminology increases the probability of being cited in AI-generated answer summaries (Google AI Overviews, Perplexity).

**Checkpoint — present the proposed tag list and ask:** "Any tags to add, remove, or reorder before I start drafting?" Wait for feedback, then finalise the list.

---

## Step 5 — Article Length Assessment

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

## Step 6 — Long-Form Article (Medium / LinkedIn Newsletter / Website Body)

Using the research from Step 3 and the length decision from Step 5, build the outline following this structure:

**Opening Hook (no heading):** 2–3 paragraphs. Specific scenario, data point, or moment from the author's actual experience. Close with a clear promise of what the article teaches.

**Section 1 — The Problem Most [Practitioners] Miss:** Core misconception using LANDSCAPE and PRACTITIONER MISTAKES from research.

**Section 2 — The Framework (name it):** Central reusable framework with a memorable name. Named frameworks get saved, cited, and searched. Use FRAMEWORKS and CASE STUDIES from research.

**Section 3 — Real-World Application:** Concrete examples from CASE STUDIES. Specificity builds credibility.

**Section 4 — Common Mistakes & How to Avoid Them:** Top 2–3 PRACTITIONER MISTAKES each paired with a concrete fix.

**Closing + CTA:** One actionable takeaway. CTA driving to the author's website or related content.

**If "full draft" was NOT in $ARGUMENTS:** pause, present the outline, wait for approval before writing prose.
**If "full draft" WAS in $ARGUMENTS:** proceed directly to prose.

Write the full article in Markdown. Tone: as specified in `AI-CONTEXT.md` under **Persona & Tone**. Use `##` headers. Use `**bold**` sparingly for framework terms and key data points only.

Save as `career/medium/DATE_SLUG.md`.

**Checkpoint — present the article and ask:** "Any edits to the long-form article before I generate the short-form content?" Wait for approval or "proceed" before continuing.

---

## Step 7 — Research Utilisation Summary

Append the following summary to `career/research/DATE_SLUG-research.md`:

```
## Research Utilisation Summary — Added [DATE]

Used in the [DATE] article:
  [list specific data points, frameworks, case studies used]

Available for sequels:
  [list unused SEQUEL SEEDS and unused research sections]

Suggested next article: [one-sentence pitch for the most logical sequel]
```

---

## Step 8 — Image Prompt & Visual Style

Generate a `mainImagePromptToGenerateImageUsingAI` prompt specific to this article's theme — subject matter, mood, colour palette, composition. Do not reuse prompts from previous articles.

**Checkpoint — pause and ask:** "Which visual style for this cover image?"

Present the options:
- **Lifelike** — hyper-realistic rendering, tactile and physical
- **Photo-realistic** — as if shot by a professional photographer
- **Illustration** — clean vector or editorial illustration style
- **Ghibli** — Studio Ghibli animation aesthetic, warm and painterly

Wait for the choice, then append the style as the final sentence of the image prompt.

---

## Step 9 — Optional Agents: Carousel and Image Thread

**Checkpoint — ask two questions before proceeding (skip if already specified in $ARGUMENTS):**

"Would you like me to also generate a **LinkedIn carousel** for this topic? This is a PDF with 8–12 swipeable slides — the highest-engagement format on LinkedIn with a 6.60% average engagement rate. (yes / no)"

"Would you like me to also generate a **Twitter/X image thread** for this topic? This is a series of 4–7 tweets each with a designed image card. (yes / no)"

Wait for both answers before proceeding.

**If LinkedIn carousel is confirmed:** Execute the full `draft-carousel` command for this topic, drawing from the research already saved in `career/research/DATE_SLUG-research.md`. Do not re-run Gemini research. Save outputs to `career/linkedin/DATE_SLUG-carousel.pdf`, `career/linkedin/DATE_SLUG-carousel-script.md`, and `career/linkedin/DATE_SLUG-carousel-post.md`.

Note that this carousel format uses the CAROUSEL HOOK from the Gemini research (Step 3). If a narrative structure hasn't been selected yet, pause and ask to choose one: Problem → Solution, Step-by-Step Guide, Before → After, Myth vs. Fact, or Data Story.

**If Twitter image thread is confirmed:** Execute the full `draft-imagethread` command for this topic, drawing from the same research. Do not re-run Gemini research. Pause to ask the visual style question from that command (bold typographic, data visualisation, illustration, or Ghibli). Save outputs to `career/twitter/DATE_SLUG-imagethread-script.md` and `career/twitter/DATE_SLUG-image-prompts.md`.

---

## Step 10 — LinkedIn Feed Post

Using the long-form article from Step 6 and the HOOK IDEAS from the Gemini research, write a LinkedIn post of 150–300 words. Do not run new research.

**Hook (lines 1–2):** Choose the strongest hook from research HOOK IDEAS, or write a better one. First two lines stand alone as a reason to expand. Never open with "I" or a question.

**Body:** Single-sentence paragraphs with line breaks. `**Bold**` for framework terms. Maximum 2 emojis as visual anchors. Every sentence earns its place.

**CTA:** Drive to the article specifically. One or two lines, no hedging.

No bullet lists. No more than 2 hashtags at the very end, if used at all.

Save as `career/linkedin/DATE_SLUG-post.md`.

---

## Step 11 — Twitter/X Thread

Using the same research and article, write a thread of 6–10 tweets. Extract the three most scroll-stopping data points and the most memorable analogy from the research.

**Tweet 1:** Hook. 280 characters maximum. Most counterintuitive finding or sharpest stat. Implicit promise.

**Tweets 2–N:** One idea per tweet. Numbered ("2/", "3/", etc.). Concrete, specific, quotable.

**Final tweet:** CTA to owned asset. Two lines maximum.

Save as `career/twitter/DATE_SLUG-thread.md`.

---

## Step 12 — CMS JSON

Assemble the final website JSON. First inspect the reference schema:

```bash
ls career/website/ && cat career/website/$(ls career/website/ | head -1)
```

Pull every field from what has already been generated — do not regenerate content. `title` from the article headline (outcome-oriented). `seoTitle` rewritten for search intent. `category` the approved value from Step 2 (must match `categories.md` exactly). `tags` the ordered array from Step 4. `body` the full Markdown from Step 6. `mainImagePromptToGenerateImageUsingAI` the finalised prompt with style from Step 8. `timeToRead` body word count ÷ 200, rounded.

Validate before saving: every required field present, no extra fields, syntactically valid JSON.

Save as `career/website/DATE_SLUG.json`.

---

## Step 13 — Publishing Checklist

Output the following to the terminal as the final deliverable of the pipeline:

```
PUBLISHING CHECKLIST — [Article Title]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Date slug prefix: DATE_SLUG
Category:         [approved category]
Pillar:           [pillar name]
Tags (ordered):   [tag 1], [tag 2], [tag 3], ...
Read time:        [N] min

FILES GENERATED
  ✓ career/research/DATE_SLUG-research.md    → preserved research + utilisation summary
  ✓ career/medium/DATE_SLUG.md               → publish to Medium + LinkedIn Newsletter
  ✓ career/linkedin/DATE_SLUG-post.md        → post to LinkedIn feed
  ✓ career/twitter/DATE_SLUG-thread.md       → post to Twitter/X
  ✓ career/website/DATE_SLUG.json            → upload to CMS
  [if carousel: ✓ career/linkedin/DATE_SLUG-carousel.pdf + -script.md + -carousel-post.md]
  [if imagethread: ✓ career/twitter/DATE_SLUG-imagethread-script.md + -image-prompts.md]

MANUAL STEPS REMAINING
  □ Generate cover image using the prompt saved in the JSON
     Style selected: [style]
  □ Generate OpenGraph image at your OG image tool
     Title for OG (check length): [article title]
     [if title > 60 characters: ⚠ LONG TITLE — suggested short version: [shortened title]]
     Category shown on OG: [approved category]
  [if carousel: □ Review carousel PDF — if rendering failed, use -carousel-script.md in Canva]
  [if imagethread: □ Generate images using prompts in -image-prompts.md, attach to tweets]
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
