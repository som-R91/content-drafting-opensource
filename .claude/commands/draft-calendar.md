# Draft or Update Content Calendar

You are creating or updating a content calendar for Somaditya Roy's personal branding pipeline. The calendar plans LinkedIn posts, Twitter threads, LinkedIn carousels, and long-form articles across a rolling time horizon.

Arguments provided: $ARGUMENTS

---

## Step 1 — Determine the AI for Calendar Generation

Check `AI-CONTEXT.md` for the `calendarAI` setting:
- `calendarAI: claude` — generate the calendar using your own reasoning. Skip the Gemini call in Step 3.
- `calendarAI: gemini` — delegate ideation to Gemini, then format and refine the output. Proceed to Step 3.
- `calendarAI: ask` (or setting missing) — **pause and ask:** "Should I generate the content calendar myself, or delegate the ideation to Gemini? (Claude / Gemini)" Wait for the answer.

---

## Step 2 — Gather Context

Before generating ideas, read two files to understand what already exists:

1. **`career/articles/INDEX.md`** — the full article list with status, pillar, and category for every article. Use this to: identify which pillars are over- or under-represented, find articles with status ≥ "Research Completed" that don't yet have content drafted (these are the fastest to move forward), and understand what topics have been covered recently.

2. **`career/articles/sequel-seeds.md`** — the lightweight sequel opportunity index. Any entry here is a high-priority idea because the research is already funded by prior work. Cross-reference sequel seed entries with INDEX.md to confirm whether the source article's research is available.

Do not open individual `research.md` files — all the information needed for calendar planning is in these two files.

Check whether $ARGUMENTS specifies a time horizon. If not, default to a 4-week rolling calendar.

---

## Step 3 — Generate Calendar Ideas

**If using Claude:** Read `pillars.md` from the workspace root for the canonical pillar definitions. Generate 8–12 content ideas across the two pillars. For each idea, briefly explain why this topic would resonate with the target audience (recruiters and senior PMs evaluating Somaditya for PM roles) and which pillar and category it falls under.

Prioritise in this order — sequel seeds get first pick of calendar slots, then Research Completed articles fill remaining slots, then new topics fill any gaps:
1. **Sequel seeds** from `sequel-seeds.md` — research already done, no Gemini step needed, highest ROI. Assign these to the earliest available slots.
2. **Research Completed** articles in INDEX.md not yet "Content Drafted" — Gemini step done, ready for `/draft-content`.
3. **New topics** based on pillar gaps from INDEX.md — require `/draft-research` first; schedule these in later weeks to account for the research step.

**If using Gemini:** Run the following and capture the full output:

```bash
gemini -p "You are a content strategist for a Data-Driven Senior PM and Ex-Founder building a personal brand to attract Senior PM and Head of Product roles. The content strategy has two pillars: (1) Shipping Without the Title — PM-level work done under non-PM titles, including Express Scripts, LatentView, TCS, and MoneTask Labs stories; (2) Building Catalyst — build-in-public content around a mobile app called Catalyst. Generate 10–12 content ideas for the next 4 weeks across these two pillars. For each idea provide: the topic/angle, the pillar it falls under, a one-sentence hook that could open a LinkedIn post, the best format for this topic (long-form article, carousel, or post-only), and one reason this topic specifically positions a Senior PM or Head of Product candidate above a mid-level PM. Avoid generic PM-101 content."
```

Refine Gemini's output — filter anything generic, reframe ideas that don't fit the pillars precisely, and surface any sequel opportunities from `sequel-seeds.md`.

---

## Step 4 — Assign Categories

For each idea, attempt to assign a category from the Active Categories in `categories.md`. Flag any idea that would require a new category — new categories will be confirmed when the individual piece is drafted via `/draft-research` or `/draft-content`, not here.

---

## Step 5 — Format Recommendation

For each calendar entry, recommend the best content format based on the topic type. The decision logic is: use a carousel when the topic has a named framework with 4–8 clearly separable components, because each component becomes a slide and the swipeable format drives the highest engagement; use a long-form article when the topic requires sustained argument or data-heavy analysis that doesn't reduce well to slides; use a post-only entry when the topic is timely, reactive to an industry event, or serves as a bridge between two deeper pieces.

Note which entries should also have a corresponding Twitter image thread — these are typically the same topics as carousels, since the visual design work can be adapted.

---

## Step 6 — Structure the Calendar

Present the calendar in this format for each week:

```
WEEK [N] — [Date Range]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  LONG-FORM ARTICLE (Medium / LinkedIn Newsletter / Website)
  Topic:             [specific angle, not just broad topic]
  Pillar:            [pillar name]
  Category:          [proposed category or "NEW — to be confirmed"]
  Research status:   [available at career/articles/NNN-SLUG/1-research/ / sequel seed from NNN-SLUG / not yet started]
  Hook idea:         [one sentence]
  Formats:           Article + LinkedIn Post + Twitter Thread
                     [+ Carousel? yes/no] [+ Image Thread? yes/no]

  STANDALONE POSTS (if any — weeks without a full article)
  LinkedIn post:     [topic and angle]
  Twitter thread:    [TOFU topic driving to a past article]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 7 — Checkpoint & Save

**Pause and present the full calendar to Somaditya.** Ask: "Any topics to swap, reorder, or adjust before I save this?" Wait for feedback, make any changes, then save as `career/content-calendar.md`, overwriting the previous version.

Output a confirmation with the file path and a count of pieces scheduled per pillar, plus how many have existing research files ready to use.
