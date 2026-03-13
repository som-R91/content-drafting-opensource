# Draft Website JSON (CMS Portfolio Piece)

You are creating a portfolio or proof-of-work piece for the personal website of the persona defined in `AI-CONTEXT.md`. Read that file first if you have not already done so this session — the positioning statement, content pillars, and CMS schema are all defined there. This will be saved as a JSON file that must match the CMS schema exactly. The audience is recruiters and senior hiring managers — every field must serve as evidence of capability, not just content.

The topic or project to feature is: $ARGUMENTS

Before starting, determine today's date in YYYY-MM-DD format and derive the topic slug (kebab-case, max 5–6 words, matching the slug used for the related article if one exists). These prefix all filenames this command produces.

If a long-form article draft already exists for this topic in `career/medium/`, use its content for the `body` field directly. If research exists at `career/research/YYYY-MM-DD_<topic-slug>-research.md`, load it and skip Step 5.

---

## Step 1 — Pillar Classification & Portfolio Positioning

Classify the piece into exactly one of the three content pillars defined in `AI-CONTEXT.md`.

Then state explicitly: what specific capability claim does this piece make about the author, and what evidence does it present to support that claim? Website pieces are evidence artefacts, not articles.

---

## Step 2 — Schema Reference Check

Inspect existing website JSON files to confirm the exact schema in use before generating anything:

```bash
ls career/website/ && cat career/website/$(ls career/website/ | head -1)
```

Note every field name, data type, and nesting structure precisely. Do not invent fields. Do not omit fields. The schema is the contract.

If `career/website/` is empty, refer to the **CMS Schema** section in `AI-CONTEXT.md` for the required fields.

---

## Step 3 — Category Assignment

Read `categories.md` from the workspace root. Propose one category from the existing Active Categories list. If no existing category fits well, propose a new one and **pause for explicit approval before continuing.** Once approved, update `categories.md` — add to Active Categories and log in the Category Addition Log table with today's date.

---

## Step 4 — Tag Generation

Generate 8–10 tags ordered strictly from most to least relevant using the following priority logic:

The first tag is the piece's primary topic keyword — the most precise single term describing what this piece is fundamentally about. Tags two and three are the methodology or framework demonstrated. Tags four through six are supporting domain concepts directly addressed in the body. Remaining tags are adjacent topics a reader of this piece would also care about.

All tags: lowercase, hyphens for multi-word terms, real practitioner vocabulary only. This ordering is intentional — the CMS and SEO crawlers weight earlier array items more heavily, and AI answer engines (Google AI Overviews, Perplexity) favour precisely-matched domain terminology over generic descriptors.

---

## Step 5 — Research (skip if article draft or research file already exists)

Replace `[YOUR ROLE/PROFESSION]` with the role description from `AI-CONTEXT.md` before running.

```bash
gemini -p "You are a research assistant helping a [YOUR ROLE/PROFESSION] write a portfolio case study for a personal website. Research the following topic and return: (1) INDUSTRY BENCHMARKS — standard metrics or performance levels so the author's outcomes can be contextualised, (2) INSIDER TERMINOLOGY — precise technical and business terms that practitioners use among themselves, (3) OUTCOME SIGNALS — specific types of outcomes that senior practitioners and hiring managers consider high-signal proof of competence, (4) RELATED FRAMEWORKS — widely-recognised frameworks or methodologies relevant to this work. Topic: $ARGUMENTS"
```

Save the output to `career/research/YYYY-MM-DD_<topic-slug>-research.md`.

---

## Step 6 — Generate the JSON

Using the schema confirmed in Step 2, the approved category from Step 3, and the ordered tags from Step 4, generate the complete JSON object:

**title:** Specific and outcome-oriented. Not "Retention Strategy" but "How I Reduced 30-Day Churn by 18% Using Behavioral Cohort Segmentation." The title is the headline a recruiter sees first.

**seoTitle:** Rewritten for search intent. Think: what would a recruiter searching for a portfolio piece on this topic actually type? Include 1–2 primary keywords naturally.

**category:** Exactly one value from the approved Active Categories in `categories.md`. Must match the registry precisely, character for character.

**tags:** The ordered array from Step 4. Most relevant first, least relevant last.

**body:** If a `career/medium/` article draft exists, use its Markdown content here directly. If not, write a structured case study of 400–700 words covering: business context and problem, approach and methodology with specific tools and frameworks named, outcome with metrics wherever possible, and one extracted principle or learning. Write in the author's authoritative first-person voice, consistent with the tone defined in `AI-CONTEXT.md`.

**mainImagePromptToGenerateImageUsingAI:** A detailed, contextually specific image generation prompt for this piece's theme. Do not reuse prompts from other articles. Then **pause and ask:** "Which visual style — **lifelike**, **photo-realistic**, **illustration**, or **Ghibli**?" Append the chosen style as the final instruction.

**timeToRead:** Integer. Body word count ÷ 200, rounded to the nearest minute.

---

## Step 7 — Validate and Save

Before saving, verify: every required field from the reference schema is present and correctly typed, no extra fields were added, and the JSON is syntactically valid (no trailing commas, all strings properly escaped).

Then ask yourself: would a senior hiring manager in the target industry read this and want to reach out? If not, identify the weakest field and strengthen it before saving.

Save as `career/website/YYYY-MM-DD_<topic-slug>.json`. Output the complete JSON and the finalised image prompt to the terminal.
