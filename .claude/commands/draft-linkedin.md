# Draft LinkedIn Post

You are writing a **short-form LinkedIn feed post** for Somaditya Roy, a Data-Driven Senior PM & Ex-Founder. This is the scroll-stopping teaser that lives in the LinkedIn feed — not the newsletter article. Its job is to drive saves and clicks through to the long-form article on the website, Medium, or LinkedIn Newsletter.

The topic or angle is: $ARGUMENTS

Before starting, normalize $ARGUMENTS to lowercase and derive the topic slug (kebab-case, max 5–6 words, matching the slug used for the related article if one exists). Read `career/articles/INDEX.md` to find the matching `NNN-SLUG` folder (case-insensitive). Store this as **FOLDER**.

If a long-form article draft already exists at `career/articles/FOLDER/3-medium/medium.md`, use it as source material and skip Step 2. If research exists at `career/articles/FOLDER/1-research/research.md`, use that instead of running new research. Only run Step 2 if neither exists.

---

## Step 1 — Pillar Classification

Read `pillars.md` from the workspace root for the canonical pillar definitions. Classify the topic into exactly one of the two pillars defined there. State the chosen pillar before proceeding.

---

## Step 2 — Research (skip if article draft or research file already exists)

If no research file exists at `career/articles/FOLDER/1-research/research.md` and no article draft exists at `career/articles/FOLDER/3-medium/medium.md`, **stop here** and output:

"No research found for this topic. Run `/draft-research <topic>` first, complete the Gemini Deep Research and Summarization steps, save the output to `career/articles/FOLDER/1-research/research.md`, then return to this command."

Do not proceed until research is available.

---

## Step 3 — Draft the Post

Write a LinkedIn post between 150 and 300 words using the five-part structure below. Every part has a distinct job — do not conflate them or skip any.

**Hook (line 1):** This is what appears before the "…see more" cutoff. It must stop the scroll entirely on its own. Use one of: a contrarian claim that challenges what most PMs believe, a striking specific stat followed by its implication, or a concrete scenario the target reader will recognise from their own experience. Never open with "I" as the first word. Never open with a question — questions signal uncertainty; statements signal authority. The LinkedIn algorithm gives three to five times more processing weight to the first sentence than to any other line in the post, so this sentence is the single highest-leverage word in the entire piece.

**Rehook (line 2–3):** This is the element most posts omit, and it is what separates good posts from viral ones. The rehook expands on the hook but intensifies the curiosity rather than satisfying it. It makes the reader feel they *must* see the next line. Think of it as the hook's acceleration — it adds a second reason to keep reading before the reader has even entered the body. Example: hook says "Most PMs measure the wrong retention metric." Rehook says "And it's costing them their product roadmap credibility with the CEO."

**Body (value section):** This is the meat. Deliver the promised insight using a reusable framework, a structured teardown, or a checklist — content the reader will want to save for later. Single-sentence paragraphs with line breaks between each. Bold key framework terms using `**asterisks**`. Use 1–2 emojis maximum placed at the start of a line as visual anchors, not decoration. Everything here must feel like it comes from someone who has shipped products and run a startup, not someone summarising an article.

**Value close (1–2 lines before CTA):** Crystallise the single most important takeaway in one sentence. This is what the reader screenshots even if they don't click the CTA.

**CTA:** Drive to the owned asset with specificity — not "check out my article" but "Full framework on my website — link in bio" or "I broke this down in depth in this week's newsletter — link in comments." The CTA should feel like a natural conclusion, not a sales pitch.

No generic PM-101 observations. No "As a PM I've learned that…" openers. No bullet lists.

**Hashtags:** Add 3–5 hashtags at the very end of the post, on their own line, after the CTA. Do not place hashtags anywhere else in the post. Use this mix:
- 1–2 broad reach tags (e.g. `#productmanagement`, `#product`, `#startup`, `#productleadership`)
- 1–2 niche tags specific to the post's core topic (e.g. `#retentionmetrics`, `#cohortanalysis`, `#northstarmetric`)
- 1 pillar-specific recurring tag: use `#BuildingCatalyst` for Pillar 2 content, or `#ShippingWithoutTheTitle` for Pillar 1 content

---

## Step 4 — Save

Save as `career/articles/FOLDER/4-linkedin/post.md`. Output the full post to the terminal.
