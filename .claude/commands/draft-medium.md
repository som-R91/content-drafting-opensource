# Draft Long-Form Article

You are writing a long-form article for Somaditya Roy, a Data-Driven Senior PM & Ex-Founder. This single Markdown file serves three destinations simultaneously: Medium, the LinkedIn Newsletter, and the `body` field of the Sanity CMS website post. The content is identical across all three — only the publishing interface differs.

The topic or angle is: $ARGUMENTS

Before doing anything else, normalize $ARGUMENTS to lowercase and derive the topic slug (kebab-case, max 5-6 words, descriptive of the article's specific angle — not just the broad topic). Read `career/articles/INDEX.md` to find the matching `NNN-SLUG` folder (case-insensitive). Store this as **FOLDER**.

If no match is found in INDEX.md: output — "SLUG not found in INDEX.md. Run `/draft-research <topic>` first to create the article folder."

If research already exists at `career/articles/FOLDER/1-research/research.md`, load it and skip Step 2. If a research file exists on the same topic, ask: "I found research for [FOLDER]. Use it, or run fresh research?" and wait for the answer.

---

## Step 1 — Pillar Classification & Article Positioning

Read `pillars.md` from the workspace root for the canonical pillar definitions. Classify the topic into exactly one of the two pillars defined there.

Then write a single positioning sentence: who is the specific reader, what problem do they have right now, and what will they be able to do after reading this that they couldn't before? This sentence anchors every writing decision that follows.

---

## Step 2 — Research Required (skip if research file already loaded)

If no research file exists at `career/articles/FOLDER/1-research/research.md`, **stop here** and output:

"No research found for this topic. Run `/draft-research <topic>` first, complete the Gemini Deep Research and Summarization steps, save the output to `career/articles/FOLDER/1-research/research.md`, then return to this command."

Do not proceed until research is available. Once loaded, confirm the file path and approximate word count before continuing.

---

## Step 2b — Pre-Validation Check (optional but recommended)

Before building the outline, consider whether this topic can be pre-validated — that is, whether there is already evidence that content on this angle resonates with a similar audience. Pre-validated content has a meaningful head start because it's built on a framework that an audience has already demonstrated interest in, rather than one you're testing from scratch.

The approach: check whether $ARGUMENTS or the research output references any well-known frameworks, named methodologies, or practitioner concepts that have already generated significant engagement elsewhere (on LinkedIn, in books, in popular articles). If the Gemini research surfaced frameworks with clear names and origins in the FRAMEWORKS section, these are signals that the underlying idea has already been validated by its audience.

If a strong pre-validated angle exists, note it explicitly before the outline: "This article is built on a pre-validated framework: [framework name], which has demonstrated resonance with [type of audience] in [context]." Then make sure the outline prominently features that named framework and adds Somaditya's own original spin — a renamed component, an adapted version, or a specific application from his MoneTask Labs or PM experience. The goal is not to copy but to adapt a proven structure to a new author's unique perspective and evidence.

If no obvious pre-validated angle exists, note that and proceed normally.

---

## Step 3 — Category Assignment

Read `categories.md` from the workspace root. Propose one category from the existing Active Categories. If no existing category fits well, propose a new one (noun phrase, specific but broad enough for future articles to share it) and **pause for Somaditya's approval before continuing.** Once approved, update `categories.md` — add to Active Categories and log in the Category Addition Log with today's date and this article's working title.

---

## Step 4 — Tag Generation

Using the research, generate 8–10 tags ordered from most to least relevant:

The first tag is the article's primary topic keyword — what a recruiter or senior PM would type into Google to find exactly this piece. Tags two and three are the primary methodology or framework. Tags four through six are supporting domain concepts. Remaining tags are adjacent context a reader of this piece would also care about.

All tags: lowercase, hyphens for multi-word terms (e.g., `north-star-metric`, `churn-cohort-analysis`), real practitioner vocabulary only. This ordering matters because LinkedIn, Medium, Sanity CMS, and search crawlers all weight earlier array items more heavily.

---

## Step 5 — Article Length Assessment & Sequel Planning

Before building the outline, read the full research output and assess how much material exists relative to a standard 1,200–1,800 word article (a 6–9 minute read, which is the engagement sweet spot for Medium and LinkedIn Newsletter).

Count the major ideas, framework components, and case studies in the research. If the material would comfortably fill more than 2,000 words without padding, flag this explicitly: "This research contains enough material for [N] articles. I recommend covering [specific sections] in this article and saving [specific sections] for a sequel." List the proposed sequel topics from the SEQUEL SEEDS section of the research.

Then ask: "Should I write this as a single 1,200–1,800 word article (recommended), a longer 2,000–2,500 word deep-dive, or split it into a Part 1 now with a Part 2 later?" Wait for the answer before building the outline.

---

## Step 6 — Build the Outline

Construct the outline following this structure. For a Part 1 of a multi-part series, note clearly in the outline which material is reserved for future parts.

**Opening Hook (no heading):** 2–3 paragraphs. Open with a specific concrete scenario, data point, or moment from Somaditya's actual experience. Establish urgency. Close with a clear promise of what the article teaches.

**Section 1 — The Problem Most PMs Miss:** The core misconception or gap. Use LANDSCAPE and PRACTITIONER MISTAKES from research.

**Section 2 — The Framework (name it):** The central reusable framework with a memorable name. Named frameworks get saved, cited, and searched. Explain each component using the FRAMEWORKS and CASE STUDIES from research.

**Section 3 — Real-World Application:** One or two concrete examples from the CASE STUDIES.

**Section 4 — Common Mistakes & How to Avoid Them:** Top 2–3 mistakes from PRACTITIONER MISTAKES. Each paired with a concrete fix.

**Closing + CTA:** One actionable takeaway. CTA driving to Somaditya's website or a related piece.

**Pause here** and present the outline for approval — unless $ARGUMENTS includes "full draft", in which case proceed directly to Step 7.

---

## Step 7 — Write the Full Draft

Write the complete article in Markdown following the approved outline. Tone throughout: authoritative, pragmatic, metrics-grounded, from lived experience. No hedging. No generic openers.

Use `##` for section headers. Use `**bold**` sparingly for framework terms and key data points only.

---

## Step 8 — Research Utilisation Summary

After completing the draft, produce a short Research Utilisation Summary and append it to `career/articles/FOLDER/1-research/research.md`:

```
RESEARCH UTILISATION — [Article Title]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Used in this article:
  - [list the specific data points, frameworks, case studies used]

Available for sequels:
  - [list the unused SEQUEL SEEDS and any unused research sections]

Suggested next article: [one-sentence pitch for the most logical sequel]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 9 — Image Prompt & Visual Style Checkpoint

Generate a detailed `mainImagePromptToGenerateImageUsingAI` prompt specific to this article's theme — subject matter, mood, colour palette, composition. Do not reuse prompts from previous articles.

**Pause and ask:** "Which visual style for this cover image — **lifelike**, **photo-realistic**, **illustration**, or **Ghibli**?" Append the chosen style as the final sentence of the prompt.

---

## Step 10 — Save All Outputs

Save the following files:
- `career/articles/FOLDER/1-research/research.md` — append the Research Utilisation Summary from Step 8
- `career/articles/FOLDER/3-medium/medium.md` — the full article draft

Output to the terminal: the article in full, the category, the ordered tag list, the finalised image prompt (with style), the read time estimate (word count ÷ 200, rounded), and the Research Utilisation Summary.
