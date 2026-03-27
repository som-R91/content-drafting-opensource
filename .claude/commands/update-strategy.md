# Update Strategy — Revisit and Revise Content Strategy

This command helps users who have been running the pipeline revisit, assess, and safely revise their content strategy. It presents a pipeline health report and runs a change impact analysis on all unpublished content before modifying any files.

Arguments: $ARGUMENTS

---

## Step 0 — Guard: Onboarding Check

Read `AI-CONTEXT.md`. If `{{YOUR_NAME}}` placeholder is still present in the Workspace Identity section, stop and output:

```
ONBOARDING NOT COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━
Run /onboard first to set up your workspace before running /update-strategy.
━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 1 — Data Collection (silent)

Read all of the following in parallel. Do not output anything to the user during this step:

- `career/articles/INDEX.md` — full article pipeline
- `career/articles/sequel-seeds.md` — sequel opportunities
- `career/content-calendar.md` — current calendar (if file exists; skip silently if not)
- Memory file `strategy_positioning.md` — current strategy (read from the memory directory Claude Code uses for this project)
- `pillars.md` — current pillar definitions

Check whether `pillars.md` and `categories.md` contain filled-in content or placeholders.

---

## Step 2 — Strategy Health Report

Present the report immediately after data collection:

```
STRATEGY HEALTH REPORT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PIPELINE STATUS
  Total articles:                    [N]
  Published:                         [N]
  Content drafted, unpublished:      [N]
  Research completed, not drafted:   [N]
  Folder created, no research yet:   [N]

PILLAR DISTRIBUTION (unpublished content only)
  [Pillar 1 name]:                   [N] articles
  [Pillar 2 name]:                   [N] articles
  [Flag if ratio is >70/30: "Note: heavy imbalance toward [pillar name]"]

SEQUEL SEEDS
  Available:                         [N] opportunities
  [List each seed — one line per entry from sequel-seeds.md]

CONTENT CALENDAR
  [If career/content-calendar.md exists: "Last calendar covers [date range].
   [N] scheduled pieces not yet drafted."]
  [If no calendar: "No saved content calendar. Run /draft-calendar after
   this session to create one."]

ESTIMATED WEEKS OF PIPELINE AHEAD
  [Drafted but unpublished + sequel seeds using existing research]
  ~[N] weeks of near-ready content

CURRENT STRATEGY
  Positioning:  [positioning statement from AI-CONTEXT.md or memory]
  Target:       [target roles from AI-CONTEXT.md]
  Objective:    [content objective from strategy_positioning.md]
  Horizon:      [time horizon from strategy_positioning.md]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 3 — Strategy Change Interview

After presenting the health report, ask:

```
WHAT DO YOU WANT TO CHANGE?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
What prompted this review? You can describe:

  — A new goal or target role you are now aiming for
  — A pillar that isn't working or that you want to replace
  — A new project you've started that should become a pillar
  — A change in positioning (how you want to be seen)
  — A different audience you now want to reach
  — A timeline change (accelerate, slow down, pause)
  — Something else

Or type "just reviewing" if you want to see the analysis first
without committing to any specific change.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Wait for response.

If "just reviewing": skip the Change Impact Analysis and instead output a brief strategic observation — note any imbalances, risks, or opportunities visible in the health report. Suggest `/draft-calendar` if no calendar exists. End with: "No changes made. Run /update-strategy again when you're ready to revise."

---

## Step 4 — Change Impact Analysis

For each unpublished article in `INDEX.md` (any status other than `Published`), classify its alignment with the proposed change:

- **ALIGNED** — fits the new direction well; continue as planned
- **PARTIAL** — fits one pillar or serves as awareness content, but the angle may need light reframing
- **MISALIGNED** — would not serve the new strategy; publishing would dilute the new positioning

For PARTIAL: offer a one-sentence reframe option.
For MISALIGNED: offer three options: (a) shelve — research is preserved if strategy changes again; (b) publish before pivoting — closes the current arc cleanly; (c) significant reframe — brief suggestion.

Then assess sequel seeds:

```
CHANGE IMPACT ANALYSIS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Proposed change: [one-sentence summary of what they want to change]

UNPUBLISHED CONTENT
  [NNN-slug]  ([status])  →  ALIGNED
    [one sentence: why it fits]

  [NNN-slug]  ([status])  →  PARTIAL
    [one sentence: the partial fit]
    Reframe option: [brief suggestion]

  [NNN-slug]  ([status])  →  MISALIGNED
    [one sentence: why it doesn't fit]
    Options: (a) Shelve  (b) Publish before pivot  (c) Reframe: [brief suggestion]

SEQUEL SEEDS
  Survive the new strategy:   [list titles]
  Become irrelevant:          [list titles]

RECOMMENDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Choose exactly one of these three recommendations based on the analysis:

**RECOMMEND PIVOT**
Pipeline is short and/or the majority of unpublished content aligns with the new direction. Pivoting now makes sense. [N] articles align, [N] are misaligned. Suggested approach: [specific plan for the misaligned articles].

**RECOMMEND FINISHING PIPELINE FIRST**
You have [N] near-ready articles that align with your current strategy. Consider completing the current arc ([N] weeks of content) before pivoting — this avoids waste and gives the current positioning a real test before changing course. Estimated pivot date: [date based on pipeline size at 1 article/week].

**PARTIAL PIVOT POSSIBLE**
[N] articles align with the new strategy. [N] need reframing. [N] should be shelved or published before pivot. You can change Pillar [1 or 2] now while keeping Pillar [1 or 2] intact. Suggested approach: [specific plan].

---

## CHECKPOINT — Confirm Before Any Changes

```
CONFIRM BEFORE CHANGES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
No files have been changed yet.

  A — Accept the recommendation and apply all changes
  B — Make partial changes (describe which)
  C — Cancel — keep everything as is

What would you like to do?
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

If C: output "No changes made. Your strategy files are unchanged." and stop.

If B: ask the user to describe which subset of changes to apply, then confirm the specific scope before proceeding.

---

## Step 5 — Apply Changes

Apply confirmed changes in this order. Announce each file before editing it.

### 5a — `memory/strategy_positioning.md`
Update with the new positioning statement, target roles, content objective, time horizon. Replace the 8-week content sequence with a revised one that priorities aligned content first, then new topics from the new pillars.

### 5b — `pillars.md`
If a pillar is being replaced: replace that pillar's definition entirely. Preserve the unchanged pillar verbatim. Add a comment line at the bottom: `<!-- Pillar [1 or 2] revised [today's date] — previous: [old name] -->`.

### 5c — `AI-CONTEXT.md`
Update the Workspace Identity section (positioning statement, target roles) and the Two Content Pillars section. Do not modify any generic section.

### 5d — `CLAUDE.md`
Update the positioning line in the Workspace Overview section.

### 5e — `categories.md`
Only if the new strategy introduces a domain not covered by existing categories: propose 1–3 new starter categories, pause for approval, then add to Active Categories and log in the Category Addition Log.

---

## Step 6 — Suggested Next Steps

After applying changes:

```
SUGGESTED NEXT STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Strategy files updated. Recommended content sequence:

IMMEDIATE (use existing research or drafts):
  [list ALIGNED and PARTIAL articles in recommended publish order]

NEXT (requires /draft-research):
  1. [new topic suggestion for the new strategy, derived from revised pillars]
  2. [second suggestion]
  3. [third suggestion if applicable]

Run /draft-calendar to generate a full 4-week calendar
reflecting your updated strategy.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```