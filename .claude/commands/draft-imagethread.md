# Draft Twitter/X Image Thread

You are creating a Twitter/X image thread for the persona defined in `AI-CONTEXT.md`. Read that file first if you have not already done so this session — the positioning statement, tone, content pillars, and voice characteristics are all defined there. Twitter does not support native carousels — the equivalent format is an image thread: a sequential series of tweets where each tweet contains a designed image card alongside a short caption. Each image must be compelling enough to stop a scroll on its own, while the thread as a whole tells a coherent story. The goal is TOFU reach — capturing cold audience attention and funnelling readers toward the owned long-form asset (website or Medium/LinkedIn Newsletter).

The topic or angle is: $ARGUMENTS

If research already exists in `career/research/` for this topic (same date prefix or recent file), load it now and skip Step 2. If a long-form article draft already exists in `career/medium/`, use it as the source and skip Step 2.

---

## Step 1 — Pillar Classification & Thread Format

Classify the topic into exactly one of the three content pillars defined in `AI-CONTEXT.md` and state it before proceeding.

Then select the thread format. Twitter image threads work best with 4–7 tweets (including the hook and CTA tweets) — longer than this and completion drops sharply on mobile. Choose the format that fits the content:

- **Stat + Insight**: Each tweet pairs a data point with a one-line practitioner implication. Best for data-heavy topics.
- **Framework Breakdown**: Each tweet covers one component of a named framework with a visual representation. Best for structured methodologies.
- **Mistake → Fix**: Each tweet names a common error and shows the corrected approach side-by-side. Best for misconception topics.
- **Story Arc**: Tweets follow a narrative — setup, complication, resolution — each illustrated. Best for personal career stories or case studies.

State the chosen pillar and thread format with a brief rationale.

---

## Step 2 — Research (skip if research file or article draft already exists)

Replace `[YOUR ROLE/PROFESSION]` with the role description from `AI-CONTEXT.md` before running.

```bash
gemini -p "You are a research assistant for a [YOUR ROLE/PROFESSION] creating a Twitter image thread — a series of 4-7 tweets each containing a designed image card. Research the following topic and return content optimised for punchy visual social cards: (1) THREAD HOOK: one counterintuitive fact or striking stat (with source) powerful enough to make a senior practitioner stop scrolling, (2) CARD IDEAS: 4-5 self-contained ideas, each expressible as a bold headline plus 1-2 supporting sentences — these become individual tweet image cards, (3) VISUAL METAPHOR: one memorable visual analogy that simplifies the core concept (e.g. 'retention is like a leaky bucket'), (4) REAL EXAMPLE: one specific company or product with a named outcome, (5) THREAD CTA: the most compelling reason for a practitioner to click through to the full article on this topic — what will they learn that they can't get from the thread alone? Topic: $ARGUMENTS"
```

Save the raw output to `career/research/YYYY-MM-DD_<topic-slug>-research.md` before proceeding. Replace YYYY-MM-DD with today's actual date.

---

## Step 3 — Tweet & Image Card Script

Write the full thread script. For each tweet, specify: the tweet number, the tweet caption text (max 240 characters, leaving room for the image), and the image card specification — a precise visual description that could be handed to a designer or used as an AI image generation prompt.

**Tweet 1 (Hook tweet):** The caption uses the THREAD HOOK stat or counterintuitive fact. Frame it as a bold claim — not a question. The image card should visualise the stat or contrast (e.g., two numbers side by side, a simple chart, a bold typographic treatment). End the caption with "(thread 🧵)" to signal there's more. Hard limit: 240 characters for the caption.

**Tweets 2–N (Body tweets):** Each tweet caption is one tight insight — a single sentence or two, no more. The image card for each should be visually distinct from the previous but consistent in brand style (same typeface, same colour palette, same logo placement). Use the VISUAL METAPHOR from research in whichever tweet it fits most naturally. Number each tweet visibly in the caption: "2/ ", "3/ ", etc.

**Final tweet (CTA tweet):** Caption drives to the owned asset specifically — not "check out my blog" but a specific, value-forward invitation. The image card can be a simple branded closing card with the author's name, the article title, and website URL.

---

## Step 4 — Image Generation Prompts

For each image card in Step 3, write a detailed AI image generation prompt that specifies: the visual concept, colour palette (consistent across all cards), typography treatment (bold headline text, readable at small sizes on mobile), and style. All cards in the thread must feel like they belong to the same visual system — same style, same brand.

**Pause here and ask:** "Which visual style for this image thread — **bold typographic** (text-dominant, high contrast), **data visualisation** (charts and graphs aesthetic), **illustration** (clean vector editorial), or **Ghibli** (warm painterly)?"

Wait for the style choice, then apply it consistently across all image card prompts.

---

## Step 5 — Save All Outputs

Save the following files (use today's date for YYYY-MM-DD):

- `career/research/YYYY-MM-DD_<topic-slug>-research.md` — raw Gemini research output (if Step 2 was run)
- `career/twitter/YYYY-MM-DD_<topic-slug>-imagethread-script.md` — the full thread script including tweet captions and image card specifications
- `career/twitter/YYYY-MM-DD_<topic-slug>-image-prompts.md` — the AI image generation prompts for each card, ready to paste into an image generator

Note in the output that images need to be generated externally (Gemini Image, Midjourney, DALL-E, or similar) using the prompts in the image-prompts file, then attached to each tweet in sequence when posting.

Output a summary listing all saved files, the tweet count, and the hook from Tweet 1.
