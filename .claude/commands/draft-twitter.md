# Draft Twitter/X Thread

You are writing a Twitter/X thread for the persona defined in `AI-CONTEXT.md`. Read that file first if you have not already done so this session — the positioning statement, tone, content pillars, and voice characteristics are all defined there. Twitter threads are top-of-funnel (TOFU) content — their job is to capture attention from a cold audience and funnel readers toward a deeper owned asset. Brevity, specificity, and a strong hook are everything on Twitter. Every tweet must earn its place.

The topic or angle is: $ARGUMENTS

Before starting, determine today's date in YYYY-MM-DD format and derive the topic slug (kebab-case, max 5–6 words, matching the slug used for the related article if one exists). These prefix all filenames this command produces.

If a long-form article draft already exists in `career/medium/` for this topic, extract from it and skip Step 2. If research exists at `career/research/YYYY-MM-DD_<topic-slug>-research.md`, use that instead. Only run Step 2 if neither exists.

---

## Step 1 — Pillar Classification

Classify the topic into exactly one of the three content pillars defined in `AI-CONTEXT.md` and state it before proceeding.

---

## Step 2 — Research (skip if article draft or research file already exists)

Replace `[YOUR ROLE/PROFESSION]` with the role description from `AI-CONTEXT.md` before running.

```bash
gemini -p "You are a research assistant for a [YOUR ROLE/PROFESSION] writing a Twitter thread. Research the following topic and return ONLY: (1) 3-5 specific, punchy data points or stats that would stop a senior practitioner mid-scroll — cite sources, (2) the single most counterintuitive fact on this topic, (3) one memorable analogy or mental model that simplifies a complex idea in one sentence, (4) names of 1-2 real companies or products with specific outcomes. Keep everything brief — this is for a social thread. Topic: $ARGUMENTS"
```

Save the output to `career/research/YYYY-MM-DD_<topic-slug>-research.md`.

---

## Step 3 — Draft the Thread

Write a thread of 6–10 tweets. Every tweet is a standalone unit — if someone screenshots a single tweet from the middle of the thread, it should still make complete sense and feel worth sharing.

**Tweet 1 (the hook):** Use the counterintuitive finding or the most striking stat from the research. Format: bold claim or surprising number → implicit promise that the thread delivers the explanation. Hard limit: 280 characters. Test it: would a senior practitioner in the target audience stop scrolling for this?

**Tweets 2 through N (the body):** Each tweet delivers exactly one idea. No padding. Prefer concrete over abstract. Use the analogy or mental model to explain the hardest concept. Number each tweet visibly: "2/", "3/", and so on.

**Final tweet (the CTA):** Drive to the owned asset directly. "Full breakdown on my site → link in bio." One or two lines maximum.

Tone: as defined in `AI-CONTEXT.md` under **Persona & Tone**. Vague claims get ignored while precise ones get retweeted.

---

## Step 4 — Save

Save the thread as `career/twitter/YYYY-MM-DD_<topic-slug>-thread.md`. Output the full thread to the terminal.
