# Draft LinkedIn Post

You are writing a **short-form LinkedIn feed post** for the persona defined in `AI-CONTEXT.md`. Read that file first if you have not already done so this session — the positioning statement, tone, content pillars, and voice characteristics are all defined there. This is the scroll-stopping teaser that lives in the LinkedIn feed — not the newsletter article. Its job is to drive saves and clicks through to the long-form article on the website, Medium, or LinkedIn Newsletter.

The topic or angle is: $ARGUMENTS

Before starting, determine today's date in YYYY-MM-DD format and derive the topic slug (kebab-case, max 5–6 words, matching the slug used for the related article if one exists). These prefix all filenames this command produces.

If a long-form article draft already exists for this topic in `career/medium/`, use it as source material and skip Step 2. If research exists at `career/research/YYYY-MM-DD_<topic-slug>-research.md`, use that instead of running new research. Only run Step 2 if neither exists.

---

## Step 1 — Pillar Classification

Classify the topic into exactly one of the three content pillars defined in `AI-CONTEXT.md` and state it before proceeding.

---

## Step 2 — Research (skip if article draft or research file already exists)

Replace `[YOUR ROLE/PROFESSION]` with the role description from `AI-CONTEXT.md` before running.

```bash
gemini -p "You are a research assistant for a [YOUR ROLE/PROFESSION] writing a LinkedIn post. Research the following topic and return ONLY: (1) 2-3 specific data points or stats with sources, (2) the most common practitioner mistake or misconception, (3) one contrarian or non-obvious angle that experienced practitioners would find valuable, (4) one reusable framework or checklist idea. Keep it tight — this is for a 150-300 word social post. Topic: $ARGUMENTS"
```

Save the output to `career/research/YYYY-MM-DD_<topic-slug>-research.md`.

---

## Step 3 — Draft the Post

Write a LinkedIn post between 150 and 300 words using the five-part structure below. Every part has a distinct job — do not conflate them or skip any.

**Hook (line 1):** This is what appears before the "…see more" cutoff. It must stop the scroll entirely on its own. Use one of: a contrarian claim that challenges what most practitioners believe, a striking specific stat followed by its implication, or a concrete scenario the target reader will recognise from their own experience. Never open with "I" as the first word. Never open with a question — questions signal uncertainty; statements signal authority. The 360 Brew algorithm now gives three to five times more processing weight to the first sentence than to any other line in the post, so this sentence is the single highest-leverage word in the entire piece.

**Rehook (lines 2–3):** This is the element most posts omit, and it is what separates good posts from viral ones. The rehook expands on the hook but intensifies the curiosity rather than satisfying it. It makes the reader feel they *must* see the next line. Think of it as the hook's acceleration — it adds a second reason to keep reading before the reader has even entered the body. Example: hook says "Most practitioners measure the wrong metric." Rehook says "And it's costing them their credibility with the executive team."

**Body (value section):** This is the meat. Deliver the promised insight using a reusable framework, a structured teardown, or a checklist — content the reader will want to save for later. Single-sentence paragraphs with line breaks between each. Bold key framework terms using `**asterisks**`. Use 1–2 emojis maximum placed at the start of a line as visual anchors, not decoration. Everything here must feel like it comes from someone who has done this work, not someone summarising an article.

**Value close (1–2 lines before CTA):** Crystallise the single most important takeaway in one sentence. This is what the reader screenshots even if they don't click the CTA.

**CTA:** Drive to the owned asset with specificity — not "check out my article" but "Full framework on my website — link in bio" or "I broke this down in depth in this week's newsletter — link in comments." The CTA should feel like a natural conclusion, not a sales pitch. This is the deplatforming step: every post should move at least some readers off LinkedIn and onto an owned channel (website, newsletter, Medium).

No generic introductory observations. No "As a [role] I've learned that…" openers. No bullet lists. No more than 2 hashtags at the very end, if used at all.

---

## Step 4 — Save

Save as `career/linkedin/YYYY-MM-DD_<topic-slug>-post.md`. Output the full post to the terminal.
