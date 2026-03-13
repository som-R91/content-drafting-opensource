# Draft or Update Content Calendar

You are creating or updating a content calendar for the personal branding pipeline defined in `AI-CONTEXT.md`. Read that file first if you have not already done so this session — the pillars, persona, and target audience are all defined there. The calendar plans LinkedIn posts, Twitter threads, LinkedIn carousels, and long-form articles across a rolling time horizon.

Arguments provided: $ARGUMENTS

---

## Step 1 — Determine the AI for Calendar Generation

Check `CLAUDE.md` for the `calendarAI` setting:
- `calendarAI: claude` — generate the calendar using your own reasoning. Skip the Gemini call in Step 3.
- `calendarAI: gemini` — delegate ideation to Gemini, then format and refine the output. Proceed to Step 3.
- `calendarAI: ask` (or setting missing) — **pause and ask:** "Should I generate the content calendar myself, or delegate the ideation to Gemini? (Claude / Gemini)" Wait for the answer.

---

## Step 2 — Gather Context

Before generating ideas, read the workspace to understand what already exists:

```bash
ls career/medium/ && ls career/linkedin/ && ls career/twitter/ && ls career/research/ && cat categories.md
```

The date-prefixed filenames (YYYY-MM-DD_slug format) make it easy to see chronological order and identify which topics have been covered recently. Note which pillars are over- or under-represented, and whether any research files exist without corresponding published articles (these are sequel opportunities already funded by prior research).

Check whether $ARGUMENTS specifies a time horizon. If not, default to a 4-week rolling calendar.

---

## Step 3 — Generate Calendar Ideas

**If using Claude:** Generate 8–12 content ideas across the three pillars defined in `AI-CONTEXT.md`. For each idea, briefly explain why this topic would resonate with the target audience defined in `AI-CONTEXT.md` under **Workspace Identity**, and which pillar and category it falls under. Check the existing research files — if a SEQUEL SEEDS section exists in any of them, those are high-priority ideas because the research is already done.

**If using Gemini:** Run the following and capture the full output. Before running, replace the bracketed placeholders with values from `AI-CONTEXT.md`:

```bash
gemini -p "You are a content strategist for a [YOUR POSITIONING STATEMENT] building a personal brand to attract [YOUR TARGET ROLE] roles at [YOUR TARGET COMPANY TYPE]. Generate 10-12 content ideas for the next 4 weeks across these three pillars — (1) [PILLAR 1 NAME]: [PILLAR 1 TOPICS]; (2) [PILLAR 2 NAME]: [PILLAR 2 TOPICS]; (3) [PILLAR 3 NAME]: [PILLAR 3 TOPICS]. For each idea provide: the topic/angle, the pillar it falls under, a one-sentence hook that could open a LinkedIn post, the best format for this topic (long-form article, carousel, or post-only), and one reason this topic specifically positions a senior candidate above a mid-level practitioner. Avoid generic introductory content."
```

Refine Gemini's output — filter anything generic, reframe ideas that don't fit the pillars precisely, and surface any sequel opportunities from existing research files.

---

## Step 4 — Assign Categories

For each idea, attempt to assign a category from the Active Categories in `categories.md`. Flag any idea that would require a new category — new categories will be confirmed when the individual piece is drafted via `/draft-master`, not here.

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
  Topic:          [specific angle, not just broad topic]
  Pillar:         [pillar name]
  Category:       [proposed category or "NEW — to be confirmed"]
  Existing research: [yes — career/research/DATE_SLUG-research.md / no]
  Hook idea:      [one sentence]
  Formats:        Article + LinkedIn Post + Twitter Thread
                  [+ Carousel? yes/no] [+ Image Thread? yes/no]

  STANDALONE POSTS (if any — weeks without a full article)
  LinkedIn post:  [topic and angle]
  Twitter thread: [TOFU topic driving to a past article]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 7 — Checkpoint & Save

**Pause and present the full calendar.** Ask: "Any topics to swap, reorder, or adjust before I save this?" Wait for feedback, make any changes, then save as `career/content-calendar.md`, overwriting the previous version.

Output a confirmation with the file path and a count of pieces scheduled per pillar, plus how many have existing research files ready to use.
