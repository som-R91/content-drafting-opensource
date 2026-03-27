# Draft Twitter/X Thread

You are writing a Twitter/X thread for Somaditya Roy, a Data-Driven Senior PM & Ex-Founder. Twitter threads are top-of-funnel (TOFU) content — their job is to capture attention from a cold audience and funnel readers toward a deeper owned asset. Brevity, specificity, and a strong hook are everything on Twitter. Every tweet must earn its place.

The topic or angle is: $ARGUMENTS

Before starting, normalize $ARGUMENTS to lowercase and derive the topic slug (kebab-case, max 5–6 words, matching the slug used for the related article if one exists). Read `career/articles/INDEX.md` to find the matching `NNN-SLUG` folder (case-insensitive). Store this as **FOLDER**.

If a long-form article draft already exists at `career/articles/FOLDER/3-medium/medium.md`, extract from it and skip Step 2. If research exists at `career/articles/FOLDER/1-research/research.md`, use that instead. Only run Step 2 if neither exists.

---

## Step 1 — Pillar Classification

Read `pillars.md` from the workspace root for the canonical pillar definitions. Classify the topic into exactly one of the two pillars defined there. State the chosen pillar before proceeding.

---

## Step 2 — Research (skip if article draft or research file already exists)

If no research file exists at `career/articles/FOLDER/1-research/research.md` and no article draft exists at `career/articles/FOLDER/3-medium/medium.md`, **stop here** and output:

"No research found for this topic. Run `/draft-research <topic>` first, complete the Gemini Deep Research and Summarization steps, save the output to `career/articles/FOLDER/1-research/research.md`, then return to this command."

Do not proceed until research is available.

---

## Step 3 — Draft the Thread

Write a thread of 6–10 tweets. Every tweet is a standalone unit — if someone screenshots a single tweet from the middle of the thread, it should still make complete sense and feel worth sharing.

**Tweet 1 (the hook):** Use the counterintuitive finding or the most striking stat from the research. Format: bold claim or surprising number → implicit promise that the thread delivers the explanation. Hard limit: 280 characters. Test it: would a senior PM stop scrolling for this?

**Tweets 2 through N (the body):** Each tweet delivers exactly one idea. No padding. Prefer concrete over abstract. Use the analogy or mental model to explain the hardest concept. Number each tweet visibly: "2/", "3/", and so on.

**Final tweet (the CTA):** Drive to the owned asset directly. "Full breakdown on my site → link in bio." One or two lines maximum. Add 2–3 hashtags at the end of this final tweet only — not to any other tweet. Use 1 broad tag (e.g. `#ProductManagement` or `#BuildInPublic`) + 1–2 topic-specific tags relevant to the thread's core idea.

Tone: authoritative, specific, grounded in real PM experience. Vague claims get ignored while precise ones get retweeted.

---

## Step 4 — Save

Save the thread as `career/articles/FOLDER/5-twitter/thread.md`. Output the full thread to the terminal.
