# Draft Twitter/X Image Thread

You are creating a Twitter/X image thread for Somaditya Roy, a Data-Driven Senior PM & Ex-Founder. Twitter does not support native carousels — the equivalent format is an image thread: a sequential series of tweets where each tweet contains a designed image card alongside a short caption. Each image must be compelling enough to stop a scroll on its own, while the thread as a whole tells a coherent story. The goal is TOFU reach — capturing cold audience attention and funnelling readers toward the owned long-form asset (website or Medium/LinkedIn Newsletter).

The topic or angle is: $ARGUMENTS

Before starting, normalize $ARGUMENTS to lowercase and derive the topic slug (kebab-case, max 5–6 words, matching the slug used for the related article if one exists). Read `career/articles/INDEX.md` to find the matching `NNN-SLUG` folder (case-insensitive). Store this as **FOLDER**.

If research already exists at `career/articles/FOLDER/1-research/research.md`, load it now and skip Step 2. If a long-form article draft already exists at `career/articles/FOLDER/3-medium/medium.md`, use it as the source and skip Step 2.

---

## Step 1 — Pillar Classification & Thread Format

Read `pillars.md` from the workspace root for the canonical pillar definitions. Classify the topic into exactly one of the two pillars defined there.

Then select the thread format. Twitter image threads work best with 4–7 tweets (including the hook and CTA tweets) — longer than this and completion drops sharply on mobile. Choose the format that fits the content:

- **Stat + Insight**: Each tweet pairs a data point with a one-line practitioner implication. Best for data-heavy topics.
- **Framework Breakdown**: Each tweet covers one component of a named framework with a visual representation. Best for structured methodologies.
- **Mistake → Fix**: Each tweet names a common error and shows the corrected approach side-by-side. Best for misconception topics.
- **Story Arc**: Tweets follow a narrative — setup, complication, resolution — each illustrated. Best for MoneTask Labs stories or case studies.

State the chosen pillar and thread format with a brief rationale.

---

## Step 2 — Research (skip if research file or article draft already exists)

If no research file exists at `career/articles/FOLDER/1-research/research.md` and no article draft exists at `career/articles/FOLDER/3-medium/medium.md`, **stop here** and output:

"No research found for this topic. Run `/draft-research <topic>` first, complete the Gemini Deep Research and Summarization steps, save the output to `career/articles/FOLDER/1-research/research.md`, then return to this command."

Do not proceed until research is available.

---

## Step 3 — Tweet & Image Card Script

Write the full thread script. For each tweet, specify: the tweet number, the tweet caption text (max 240 characters, leaving room for the image), and the image card specification — a precise visual description that could be handed to a designer or used as an AI image generation prompt.

**Tweet 1 (Hook tweet):** The caption uses the THREAD HOOK stat or counterintuitive fact. Frame it as a bold claim — not a question. The image card should visualise the stat or contrast (e.g., two numbers side by side, a simple chart, a bold typographic treatment). End the caption with "(thread 🧵)" to signal there's more. Hard limit: 240 characters for the caption.

**Tweets 2–N (Body tweets):** Each tweet caption is one tight insight — a single sentence or two, no more. The image card for each should be visually distinct from the previous but consistent in brand style (same typeface, same colour palette, same logo placement). Use the VISUAL METAPHOR from research in whichever tweet it fits most naturally. Number each tweet visibly in the caption: "2/ ", "3/ ", etc.

**Final tweet (CTA tweet):** Caption drives to the owned asset specifically — not "check out my blog" but "I broke down the full framework with a real MoneTask example on my site — link in bio." The image card can be a simple branded closing card with Somaditya's name, the article title, and website URL.

---

## Step 4 — Image Generation Prompts

For each image card in Step 3, write a detailed AI image generation prompt that specifies: the visual concept, colour palette (consistent with Somaditya's brand across all cards), typography treatment (bold headline text, readable at small sizes on mobile), and style. All cards in the thread must feel like they belong to the same visual system — same style, same brand.

**Pause here and ask:** "Which visual style for this image thread — **bold typographic** (text-dominant, high contrast), **data visualisation** (charts and graphs aesthetic), **illustration** (clean vector editorial), or **Ghibli** (warm painterly)?"

Wait for the style choice, then apply it consistently across all image card prompts.

---

## Step 5 — Save All Outputs

Save the following files:

- `career/articles/FOLDER/5-twitter/imagethread-script.md` — the full thread script including tweet captions and image card specifications
- `career/articles/FOLDER/5-twitter/image-prompts.md` — the AI image generation prompts for each card, ready to paste into an image generator

Note in the output that images need to be generated externally (Gemini Image, Midjourney, DALL-E, or similar) using the prompts in the image-prompts file, then attached to each tweet in sequence when posting.

Output a summary listing all saved files, the tweet count, and the hook from Tweet 1.
