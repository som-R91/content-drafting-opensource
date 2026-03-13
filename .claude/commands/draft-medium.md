# Draft Long-Form Article

You are writing a long-form article for the persona defined in `AI-CONTEXT.md`. Read that file first if you have not already done so this session — the positioning statement, tone, content pillars, and voice characteristics are all defined there. This single Markdown file serves three destinations simultaneously: Medium, the LinkedIn Newsletter, and the `body` field of the CMS website JSON. The content is identical across all three — only the publishing interface differs.

The topic or angle is: $ARGUMENTS

Before doing anything else, determine today's date in YYYY-MM-DD format and derive the topic slug (kebab-case, max 5-6 words, descriptive of the article's specific angle — not just the broad topic). These two values prefix every filename this command produces.

If research already exists at `career/research/YYYY-MM-DD_<topic-slug>-research.md`, load it and skip Step 2. If a research file exists from a recent date on the same topic, ask: "I found research from [date] on a related topic. Use it, or run fresh research?" and wait for the answer.

---

## Step 1 — Pillar Classification & Article Positioning

Classify the topic into exactly one of the three content pillars defined in `AI-CONTEXT.md` under **The Rule of Three Content Pillars**. State the chosen pillar and a one-sentence justification.

Then write a single positioning sentence: who is the specific reader, what problem do they have right now, and what will they be able to do after reading this that they couldn't before? This sentence anchors every writing decision that follows.

---

## Step 2 — Deep Research via Gemini (skip if research file already loaded)

Run the following command. Capture the complete, untruncated output and save it immediately to `career/research/YYYY-MM-DD_<topic-slug>-research.md` before any drafting begins. This preserves the research for future sessions and enables sequels without re-running Gemini.

Replace `[YOUR ROLE/PROFESSION]` with the role description from `AI-CONTEXT.md` before running.

```bash
gemini -p "You are a research assistant for a [YOUR ROLE/PROFESSION] writing an authoritative long-form article for Medium and LinkedIn Newsletter. Conduct thorough research on the following topic and return structured findings in these exact labelled sections — LANDSCAPE: the current state of practice and why it falls short for senior practitioners; DATA: at least 5-6 specific statistics or research findings with sources; FRAMEWORKS: 2-3 named frameworks or mental models including the name, origin if known, and a description of each component; CASE STUDIES: 2-3 real-world company examples with specific measurable outcomes; CONTRARIAN ANGLE: one well-reasoned position that challenges the mainstream view with supporting evidence; PRACTITIONER MISTAKES: the top 3 mistakes that mid-to-senior practitioners make on this topic, each with a concrete scenario; SEQUEL SEEDS: 2-3 related sub-topics that could each sustain their own full article — note these for potential sequels. Topic: $ARGUMENTS"
```

After saving the research file, output the file path and word count to confirm it was saved successfully.

---

## Step 2b — Pre-Validation Check (optional but recommended)

Before building the outline, consider whether this topic can be pre-validated — that is, whether there is already evidence that content on this angle resonates with a similar audience. Pre-validated content has a meaningful head start because it's built on a framework that an audience has already demonstrated interest in, rather than one you're testing from scratch.

The approach: check whether $ARGUMENTS or the research output references any well-known frameworks, named methodologies, or practitioner concepts that have already generated significant engagement elsewhere (on LinkedIn, in books, in popular articles). If the Gemini research surfaced frameworks with clear names and origins in the FRAMEWORKS section, these are signals that the underlying idea has already been validated.

If a strong pre-validated angle exists, note it explicitly before the outline: "This article is built on a pre-validated framework: [framework name], which has demonstrated resonance with [type of audience] in [context]." Then make sure the outline prominently features that named framework and adds the author's own original spin — a renamed component, an adapted version, or a specific application from their own career experience. The goal is not to copy but to adapt a proven structure to a new author's unique perspective and evidence.

If no obvious pre-validated angle exists, note that and proceed normally.

---

## Step 3 — Category Assignment

Read `categories.md` from the workspace root. Propose one category from the existing Active Categories. If no existing category fits well, propose a new one (noun phrase, specific but broad enough for future articles to share it) and **pause for explicit approval before continuing.** Once approved, update `categories.md` — add to Active Categories and log in the Category Addition Log with today's date and this article's working title.

---

## Step 4 — Tag Generation

Using the research, generate 8–10 tags ordered from most to least relevant:

The first tag is the article's primary topic keyword — what a practitioner in the target field would type into Google to find exactly this piece. Tags two and three are the primary methodology or framework. Tags four through six are supporting domain concepts. Remaining tags are adjacent context a reader of this piece would also care about.

All tags: lowercase, hyphens for multi-word terms (e.g., `north-star-metric`, `churn-cohort-analysis`), real practitioner vocabulary only. This ordering matters because LinkedIn, Medium, the CMS, and search crawlers all weight earlier array items more heavily. Precise domain terminology also increases the probability of being cited in AI-generated answer summaries (Google AI Overviews, Perplexity).

---

## Step 5 — Article Length Assessment & Sequel Planning

Before building the outline, read the full research output and assess how much material exists relative to a standard 1,200–1,800 word article (a 6–9 minute read, which is the engagement sweet spot for Medium and LinkedIn Newsletter).

Count the major ideas, framework components, and case studies in the research. If the material would comfortably fill more than 2,000 words without padding, flag this explicitly: "This research contains enough material for [N] articles. I recommend covering [specific sections] in this article and saving [specific sections] for a sequel." List the proposed sequel topics from the SEQUEL SEEDS section of the research.

Then ask: "Should I write this as a single 1,200–1,800 word article (recommended), a longer 2,000–2,500 word deep-dive, or split it into a Part 1 now with a Part 2 later?" Wait for the answer before building the outline. The saved research file means no information is ever lost — future articles will draw from it.

---

## Step 6 — Build the Outline

Construct the outline following this structure. For a Part 1 of a multi-part series, note clearly in the outline which material is reserved for future parts.

**Opening Hook (no heading):** 2–3 paragraphs. Open with a specific concrete scenario, data point, or moment from the author's actual experience. Establish urgency. Close with a clear promise of what the article teaches.

**Section 1 — The Problem Most [Practitioners] Miss:** The core misconception or gap. Use LANDSCAPE and PRACTITIONER MISTAKES from research.

**Section 2 — The Framework (name it):** The central reusable framework with a memorable name. Named frameworks get saved, cited, and searched. Explain each component using the FRAMEWORKS and CASE STUDIES from research.

**Section 3 — Real-World Application:** One or two concrete examples from the CASE STUDIES. Specificity is everything here.

**Section 4 — Common Mistakes & How to Avoid Them:** Top 2–3 mistakes from PRACTITIONER MISTAKES. Each paired with a concrete fix.

**Closing + CTA:** One actionable takeaway. CTA driving to the author's website or a related piece.

**Pause here** and present the outline for approval — unless $ARGUMENTS includes "full draft", in which case proceed directly to Step 7.

---

## Step 7 — Write the Full Draft

Write the complete article in Markdown following the approved outline. Apply the tone and voice defined in `AI-CONTEXT.md` under **Persona & Tone** consistently throughout. No hedging. No generic openers. Reference real tools, real metrics, real tradeoffs drawn from the author's actual experience. Every paragraph earns its place — if it doesn't add new information, cut it.

Use `##` for section headers. Use `**bold**` sparingly for framework terms and key data points only. This Markdown will be used verbatim on Medium, LinkedIn Newsletter, and as the CMS `body` field — formatting must be clean and portable.

---

## Step 8 — Research Utilisation Summary

After completing the draft, produce a short Research Utilisation Summary:

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

This summary is appended to the research file at `career/research/YYYY-MM-DD_<topic-slug>-research.md` so it's visible when that file is opened in a future session.

---

## Step 9 — Image Prompt & Visual Style Checkpoint

Generate a detailed `mainImagePromptToGenerateImageUsingAI` prompt specific to this article's theme — subject matter, mood, colour palette, composition. Do not reuse prompts from previous articles.

**Pause and ask:** "Which visual style for this cover image — **lifelike**, **photo-realistic**, **illustration**, or **Ghibli**?" Append the chosen style as the final sentence of the prompt.

---

## Step 10 — Save All Outputs

Save the following files using the YYYY-MM-DD_topic-slug prefix:

- `career/research/YYYY-MM-DD_<topic-slug>-research.md` — already saved in Step 2; append the Research Utilisation Summary from Step 8
- `career/medium/YYYY-MM-DD_<topic-slug>.md` — the full article draft

Output to the terminal: the article in full, the category, the ordered tag list, the finalised image prompt (with style), the read time estimate (word count ÷ 200, rounded), and the Research Utilisation Summary.
