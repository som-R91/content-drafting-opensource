# Draft LinkedIn Carousel (PDF)

You are creating a LinkedIn carousel for the persona defined in `AI-CONTEXT.md`. Read that file first if you have not already done so this session — the positioning statement, tone, content pillars, and voice characteristics are all defined there. LinkedIn carousels are uploaded as multi-page PDFs — each page becomes a swipeable slide in the feed. This format consistently achieves the highest engagement rate on LinkedIn (6.60% average by impression, per Socialinsider 2025), driven by the Ovsiankina effect: once a reader starts swiping, they feel compelled to finish. Every slide click counts as a separate engagement signal to the algorithm.

Critically, carousels and infographics are not just the highest-engagement formats — they are the formats that convert most reliably into *followers*. The reason is behavioural: readers spend more time on carousels digesting the information, taking away the value, and saving them for later, which triggers a follow. Video drives views but not follows at the same rate, because people watch and move on. The strategic goal of every carousel is therefore twofold: immediate saves (authority signal) and follower conversion (compounding reach). Design every slide with both goals in mind.

The topic or angle is: $ARGUMENTS

If research already exists in `career/research/` for this topic (same date prefix or recent file), load it now and skip Step 2. If a long-form article draft already exists in `career/medium/`, use it as the primary content source and skip Step 2.

---

## Step 1 — Pillar Classification & Carousel Type Selection

Classify the topic into exactly one of the three content pillars defined in `AI-CONTEXT.md`. State the chosen pillar with a one-sentence justification.

Then select the carousel narrative structure that best fits this topic. Each structure has a different psychological mechanism — choose the one that matches the content, not the one that's easiest to fill:

- **Problem → Solution**: Opens with a pain point the reader feels right now, builds tension through implications, resolves with a framework. Best for: contrarian takes, misconception corrections.
- **Step-by-Step Guide**: Each slide is one step in a process. Best for: execution playbooks, how-to frameworks.
- **Before → After**: Shows a transformation across slides. Best for: case studies, personal career stories, team or process improvements.
- **Myth vs. Fact**: Alternating slides debunk common misconceptions. Best for: debunking topics, data literacy, challenging received wisdom.
- **Data Story**: Leads with a striking stat, builds context slide by slide, ends with a practitioner insight. Best for: data-heavy frameworks, industry benchmarks.

State the chosen pillar and structure, with a one-sentence rationale, before proceeding.

---

## Step 2 — Research (skip if research file or article draft already exists)

Replace `[YOUR ROLE/PROFESSION]` with the role description from `AI-CONTEXT.md` before running.

```bash
gemini -p "You are a research assistant for a [YOUR ROLE/PROFESSION] creating a LinkedIn carousel — a swipeable multi-slide visual format. Research the following topic and return structured findings optimised for visual slide content: (1) HOOK STAT: one striking, specific data point that would stop a senior practitioner mid-scroll — cite the source, (2) CORE INSIGHT: the single most important non-obvious insight on this topic that an experienced practitioner would find genuinely useful, (3) FRAMEWORK: a named, structured framework (3-7 components) that can be visualised across slides — give it a name if it doesn't have one, (4) SLIDE-READY FACTS: 6-8 specific, punchy facts, stats, or principles that each stand alone as a single slide idea, (5) REAL EXAMPLE: one real company or product that illustrates the framework in action with a specific outcome, (6) COMMON MISTAKE: the single most costly mistake practitioners make on this topic, stated as a concrete scenario. Topic: $ARGUMENTS"
```

Save the raw output to `career/research/YYYY-MM-DD_<topic-slug>-research.md` before proceeding. Replace YYYY-MM-DD with today's actual date.

---

## Step 3 — Slide Script

Design a carousel of 8–12 slides. Research consistently shows that 10–12 slides is the optimal range for LinkedIn carousels targeting a professional audience — enough to deliver real value, not so many that completion rates drop. Each slide in this script should specify: the slide number, a headline (max 8 words), the body copy (max 40 words), and a layout note describing the visual composition.

Apply these rules to every slide without exception:

**Slide 1 (Cover):** This is the only slide visible in the feed before the reader swipes. It must earn the swipe. Use the HOOK STAT from research as the primary headline, or open with a bold contrarian claim. Include "→ swipe to learn" or equivalent as a micro-CTA. Keep text minimal — the cover is a billboard, not a paragraph. Design note: high contrast, large typography, consistent brand colours.

**Slides 2–N (Body):** Each slide delivers exactly one idea from the research. Never put two ideas on one slide. Use the chosen narrative structure to sequence the slides — they should feel like chapters, not a random list of tips. Alternate between data slides (leading with a stat) and insight slides (leading with a principle or framework component). Slide headlines should be readable in under 2 seconds. Body copy should be readable in under 5 seconds. White space is part of the design — do not fill every pixel.

**Second-to-last slide (Mistake slide):** Always include the COMMON MISTAKE from research as a dedicated slide. Frame it as "The mistake most practitioners make:" followed by the corrected behaviour. This slide reliably drives saves because readers want to reference it later.

**Final slide (CTA):** Do not waste the final slide on a generic "follow me." Make the CTA specific and value-oriented: "I wrote the full framework on my website — link in bio." or "Download this as a reference — save this post." Include the author's name and a consistent visual identity element (logo, colour block, tagline).

---

## Step 4 — Accompanying LinkedIn Post

Write the short LinkedIn post that will be posted alongside the PDF upload. This post is what appears above the carousel in the feed — it sets context and provides the hook before the reader even sees Slide 1.

Keep it to 3–5 lines maximum. The first line is the hook (same hook as Slide 1 or a complementary angle). The second and third lines briefly promise what the carousel delivers. The final line is a swipe prompt: "Swipe through →" or "Save this for your next planning cycle." No hashtags in the body — if used at all, place 1–2 at the very end.

---

## Step 5 — PDF Render

After the slide script is approved (pause here if running standalone — proceed directly if called from draft-master), generate the PDF using Python. First check if the required libraries are available:

```bash
pip show reportlab 2>/dev/null || pip install reportlab --break-system-packages
```

Then write and execute a Python script that renders each slide as a 1080×1080px page in a multi-page PDF. Apply these technical specifications derived from LinkedIn's current carousel requirements:

- Page dimensions: 1080×1080 pixels (square format, optimal for both mobile and desktop)
- Minimum font size: 24pt for headlines, 18pt for body copy (LinkedIn's readability threshold)
- Maximum file size: 100MB (stay well under this — target under 5MB for fast upload)
- Colour palette: use a consistent 2–3 colour scheme across all slides (do not introduce new colours mid-carousel)
- Brand consistency: same typeface, same layout grid, same logo position on every slide

Save the PDF to `career/linkedin/YYYY-MM-DD_<topic-slug>-carousel.pdf`.

If PDF rendering fails for any reason, output the full slide script as `career/linkedin/YYYY-MM-DD_<topic-slug>-carousel-script.md` so the carousel can be rendered manually in Canva or Adobe Express. Note clearly which slides need design attention.

---

## Step 6 — Save All Outputs & Summarise

Save the following files (use today's date for YYYY-MM-DD):

- `career/research/YYYY-MM-DD_<topic-slug>-research.md` — raw Gemini research output (if Step 2 was run)
- `career/linkedin/YYYY-MM-DD_<topic-slug>-carousel.pdf` — the rendered PDF carousel
- `career/linkedin/YYYY-MM-DD_<topic-slug>-carousel-script.md` — the slide script in Markdown (always save this, even when PDF renders successfully — it's the editable source)
- `career/linkedin/YYYY-MM-DD_<topic-slug>-post.md` — the accompanying LinkedIn post text

Output a summary to the terminal listing all saved files, the slide count, and one sentence on what makes the hook on Slide 1 likely to earn the swipe.
