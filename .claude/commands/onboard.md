# Onboard — First-Time Workspace Setup

This command guides a new user through complete workspace initialisation. It collects career history, derives content pillars, and generates all configuration and memory files so every other slash command works correctly from the first run.

Arguments: $ARGUMENTS

---

## Step 0 — Pre-Flight Check

Before asking the user any questions, read `AI-CONTEXT.md` and check whether `{{YOUR_NAME}}` still appears as a placeholder in the Workspace Identity section.

**If placeholders are present:** proceed with onboarding.

**If placeholders are gone** (onboarding was previously completed), output:

```
ONBOARDING ALREADY COMPLETED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
It looks like this workspace has already been set up for: [name found in AI-CONTEXT.md]

To update your strategy or pillars, use /update-strategy instead.
To re-run onboarding and overwrite everything, type: re-onboard
To cancel, type: cancel
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for a response. If the user types "re-onboard", continue with Step 1. If "cancel", stop.

---

## Step 1 — Document Collection Notice

Output the following before asking any questions:

```
BEFORE WE BEGIN — HAVE THESE READY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
The more specific your answers, the better your content system will be.
Have the following open before you continue:

  1. Your resume or CV (even a rough draft)
  2. Your LinkedIn About section (if you have one)
  3. A list of your most significant projects — including side projects
     or ventures — with outcomes and metrics where possible
  4. Your current job title and employer (or most recent, if between roles)
  5. Your target role or goal (the job you want or the audience you want to reach)

Ready to begin? (yes / not yet)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for confirmation before continuing.

---

## Step 2 — Identity and Positioning Interview

Ask all questions in a single block so the user can answer in sequence:

```
IDENTITY AND POSITIONING
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. What is your full name?

2. What is your current job title and employer?
   (Or most recent, if you are between roles.)

3. What is the target role or outcome you are building toward?
   Examples: "Senior Product Manager at a Series B startup"
             "Freelance UX consultant attracting B2B SaaS clients"
             "Thought leader in AI product development"

4. In one or two sentences: what is the gap between how your career
   looks on paper and how it actually reads to someone who knows the work?
   This gap is usually the central argument of your content.
   Example: "My title has been Data Analyst, but I've been making product
   decisions for three years."

5. What is your primary content platform?
   (LinkedIn / Twitter/X / Substack / personal blog / other)

6. Approximate follower or subscriber counts on each platform?
   (Rough ranges are fine: 0, under 500, 500–5k, 5k–50k, 50k+)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for all answers before continuing.

---

## Step 3 — Career History Interview

```
CAREER HISTORY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
For each role you've held (most recent first), provide:

  Role title and company
  Approximate dates (year start – year end is fine)
  2–3 sentences on the work that actually mattered — not the job
  description, but what you would bring up in an interview

Then separately, list any side projects, ventures, or personal projects:
  Project name and what you built
  What happened (shipped / failed / ongoing)
  The most important outcome, lesson, or metric

If you have quantified results — revenue, users, time saved, error rates,
team sizes, anything measurable — include them. These become proof points
in your content.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for the full answer.

---

## CHECKPOINT 1 — Career History Confirmation

Synthesize the career history into a structured summary and present it for confirmation:

```
CAREER HISTORY SUMMARY — PLEASE CONFIRM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Here is what I've captured. Please confirm or correct before I proceed.

Name: [name]
Current or most recent role: [role] at [company]
Target: [target role or outcome]
Core positioning argument: [one-sentence synthesis of the gap they described]

Career timeline:
  [year] — [role], [company]: [2-sentence summary of what mattered]
  [continue for all roles]

Projects:
  [project name]: [what it was, what happened, key metric or lesson]
  [continue for all projects]

Key credibility assets (specific metrics and outcomes I'll use in content):
  - [bulleted list of the most content-worthy numbers and outcomes]

Is this accurate? Any corrections, additions, or things to emphasise more?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for confirmation or corrections. If edits are requested, incorporate them and re-present only the changed sections before continuing.

---

## Step 4 — Pillar Derivation

Using the confirmed career history, derive two content pillars. Apply this logic:

- **Pillar 1** is the historical credibility pillar — the body of work from the past that proves the target claim. It answers "why should anyone believe you?" by showing the work pre-dated the credential.
- **Pillar 2** is the current activity pillar — something the user is actively doing right now that documents the transition or the target capability in real time. It answers "what are you doing about it right now?"

Present the derived pillars:

```
PROPOSED CONTENT PILLARS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Based on your career history and target, here are two content pillars.

PILLAR 1 — [proposed name, 3–5 words, specific to their narrative]
Definition:      [one sentence — what this pillar is about and why it
                 supports the positioning]
What belongs here: [2–3 sentences: the specific experiences and projects]
Core topics:     [comma-separated list of 6–10 specific topic areas]

PILLAR 2 — [proposed name, 3–5 words, specific to their current activity]
Definition:      [one sentence]
What belongs here: [2–3 sentences]
Core topics:     [comma-separated list]

Reasoning: [2–3 sentences explaining why these two pillars are the right
architecture for their goal — what tension they create, what audience they
address, and how the two pillars work together]

Do you want to proceed with these pillars, or adjust them?
  A — Accept both pillars as proposed
  B — Adjust Pillar 1 (describe what to change)
  C — Adjust Pillar 2 (describe what to change)
  D — Rethink both (describe a different direction)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## CHECKPOINT 2 — Pillar Approval

Wait for response. If B, C, or D: revise the relevant pillar(s) and re-present only the revised section. Repeat until the user confirms with A. Do not proceed to Step 5 until pillars are approved.

---

## Step 5 — Category Generation

Based on the approved pillars and career background, propose 4–6 starter categories. Apply the same rules as `categories.md` — noun phrases, title case, specific enough to be a useful website filter but broad enough for multiple future articles to share the category.

```
STARTER CATEGORIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Based on your pillars and background, here are starter categories for
your content registry. These will appear as filter options on your website.

  - [Category 1]
  - [Category 2]
  - [Category 3]
  - [Category 4]
  [and so on]

You can add more categories later during any draft command.
Accept these, or list any you want to add, remove, or rename?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for response. Incorporate any adjustments.

---

## Step 6 — Content Objective and Timeline

```
CONTENT STRATEGY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Two final questions:

1. What is the single most important thing you want content to do for you?
   Examples: "Get inbound recruiter messages for PM roles"
             "Build an audience for a course I'm planning"
             "Attract clients for my consulting practice"
             "Establish thought leadership before my job search starts"

2. Is there a specific deadline or time horizon?
   Examples: "I'm job hunting actively now"
             "I want to build for 6 months before applying"
             "No deadline — long-term brand building"
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for answers.

---

## CHECKPOINT 3 — Strategy Summary Approval

Synthesize a one-paragraph strategy statement and present it:

```
YOUR CONTENT STRATEGY SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[1-paragraph summary covering: who the user is, their positioning statement,
the two pillars and how they work together, the target outcome, the time
horizon, and the primary platform]

Does this accurately capture your content strategy?
(yes / adjust: [describe the change])
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for confirmation. If adjustment requested, revise and re-present.

---

## Step 7 — File Generation

Once all three checkpoints are cleared, generate files in sequence. Announce each file before creating it.

### 7a — `AI-CONTEXT.md`
Replace all `{{PLACEHOLDER}}` blocks with the collected information. Preserve every generic section verbatim (funnel architecture, LinkedIn algorithm, post structure, carousel strategy, research preservation policy, article length strategy, Sanity CMS schema, AI configuration settings, directory structure, tag ordering convention). Only the Workspace Identity, Persona & Tone, and Two Content Pillars sections are personalised.

The Persona & Tone section should include a specific tone description derived from the positioning gap — e.g., if the gap is "doing PM work without the title", the tone should be direct and evidence-forward; if the gap is "deep domain expert building in public", the tone should be authoritative and transparent.

### 7b — `pillars.md`
Replace with the two approved pillar definitions in the canonical format. Remove the example block entirely. The file should contain only the two pillars and the classification rule.

### 7c — `categories.md`
Replace the placeholder Active Categories list with the approved starter categories. Populate the Category Addition Log with today's date and "Onboarding" in the First Used For column for each category.

### 7d — `CLAUDE.md`
Update the Workspace Overview section: replace `{{YOUR_NAME}}`, `{{YOUR_POSITIONING_STATEMENT}}`, and `{{YOUR_TARGET_ROLES}}` placeholders with the actual values.

### 7e — Memory files
Create the following four files in the project memory directory (the `memory/` folder Claude Code uses for this project, located outside the workspace):

**`memory/user_background.md`** — Full career history in structured format:
```markdown
---
name: [NAME]'s Background & Career Context
description: Full career history, current situation, job search context. Read before any content or strategy work.
type: user
---

[Full structured career summary from the confirmed history]
```

**`memory/user_key_assets.md`** — Key credibility assets:
```markdown
---
name: [NAME]'s Key Credibility Assets
description: Specific stories, metrics, and projects. Reference before drafting content.
type: user
---

[Structured list of credibility assets with metrics, organised by role/project]
```

**`memory/strategy_positioning.md`** — Core strategy:
```markdown
---
name: Content Strategy & Positioning
description: Core positioning, content pillars, narrative arc, and 8-week content sequence.
type: project
---

**Core positioning:**
> "[positioning statement]"

**Two pillars:**
1. [Pillar 1 name] — [one-sentence definition]
2. [Pillar 2 name] — [one-sentence definition]

**Content objective:** [what content should do]
**Time horizon:** [deadline or approach]
**Primary platform:** [platform]

**Suggested 8-week content sequence:**
[Generate a suggested sequence of 8 weekly content pieces based on the two pillars and the career history, prioritising the highest-credibility stories first]

**Why:** [One paragraph explaining the strategic logic — why these pillars, this sequence, this framing]
**How to apply:** [When to reference this file and how it should shape content decisions]
```

**`memory/MEMORY.md`** — Index file:
```markdown
# Memory Index

## User
- [Background & Career Context](user_background.md) — Full career history, current situation, job search context. Read before any content or strategy work.
- [Key Credibility Assets](user_key_assets.md) — Specific stories, metrics, and projects. Reference before drafting content.

## Strategy
- [Content Strategy & Positioning](strategy_positioning.md) — Core positioning, pillars, narrative arc, and 8-week content sequence.

# currentDate
Today's date is [today's date in YYYY-MM-DD format].
```

---

## Step 8 — Completion Summary

Output:

```
ONBOARDING COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Workspace configured for: [name]
Positioning: [positioning statement]
Target: [target roles/outcome]

FILES UPDATED
  ✓ AI-CONTEXT.md           — personalised with your identity and pillars
  ✓ pillars.md              — [Pillar 1 name] + [Pillar 2 name]
  ✓ categories.md           — [N] starter categories
  ✓ CLAUDE.md               — positioning updated

MEMORY FILES CREATED
  ✓ memory/user_background.md
  ✓ memory/user_key_assets.md
  ✓ memory/strategy_positioning.md
  ✓ memory/MEMORY.md

YOUR TWO PILLARS
  Pillar 1 — [name]: [one-sentence definition]
  Pillar 2 — [name]: [one-sentence definition]

STARTER CATEGORIES
  [list all approved categories]

RECOMMENDED FIRST STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Your workspace is ready. Start the content pipeline with:

  /draft-research [your first topic]

Suggested first topics based on your strongest credibility stories:
  1. [specific angle from Pillar 1 — derived from highest-credibility story]
  2. [specific angle from Pillar 2 — derived from current project or activity]
  3. [third option if a strong topic was mentioned during the interview]

After completing the Gemini research steps, run:
  /draft-content [slug]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```