# AI-Powered Personal Branding Content Workspace

A fully automated, multi-agent content production pipeline for professionals building a personal brand. Given a topic or angle, this workspace orchestrates Claude Code and Gemini CLI to produce a long-form article, a LinkedIn feed post, a Twitter/X thread, a CMS portfolio piece, and optionally a LinkedIn carousel PDF and a Twitter image thread — all in a single coordinated pipeline with strategic checkpoints for your input.

---

## What This Is

Most personal branding workflows are fragmented: you research in one tool, draft in another, rewrite in a third, and manually copy content between platforms. This workspace replaces that fragmentation with a single orchestrated pipeline. You provide the topic. The pipeline handles the research, drafting, formatting, and file organisation — pausing at the decisions that require your judgment and automating everything else.

The pipeline is built on a deliberate division of labour between two AI tools. Gemini CLI handles deep factual research, surfacing data points, named frameworks, case studies, and contrarian angles. Claude Code takes that raw research and transforms it into finished, persona-consistent content across all formats. Research is preserved in a dedicated folder so sequel articles can be written in future sessions without re-running Gemini.

---

## Prerequisites

Before setting up this workspace, you need the following tools installed and authenticated. Both AI tools must be installed and initialised in your workspace before the pipeline will work — the research step relies on Claude Code invoking Gemini CLI as a subprocess, which will fail silently or prompt for permissions at the worst possible moment if Gemini has never been opened in this directory before.

**Claude Code** is Anthropic's agentic coding and writing assistant that runs in your terminal. It requires Node.js 18 or later. Install it globally via npm:

```bash
npm install -g @anthropic-ai/claude-code
```

You will need an Anthropic account. On first run, Claude Code will open a browser window to complete authentication. Full installation documentation is at https://docs.claude.ai/code.

**Gemini CLI** is Google's command-line interface for Gemini models. Install it globally via npm:

```bash
npm install -g @google/gemini-cli
```

You will need a Google account with Gemini API access. On first run, Gemini CLI will prompt you to authenticate via browser and will ask for permission to access your local filesystem. Full installation documentation is at https://github.com/google-gemini/gemini-cli.

**Python 3** is required for carousel PDF rendering. It is likely already installed on your system. Verify with `python3 --version`. The `reportlab` library is used for PDF generation and will be installed automatically by the carousel command if not already present.

A **CMS account** is required if you want to use the website portfolio JSON feature. The default configuration targets Sanity CMS, but the schema section in `AI-CONTEXT.md` can be updated to match any CMS or custom JSON structure. If you do not use a CMS, you can skip `/draft-website-json` entirely and use only the article, LinkedIn, and Twitter outputs.

---

## Getting Started

This section walks you through everything you need to do before running your first content session. The whole setup should take about 20–30 minutes.

### Step 1 — Clone this repository

Clone or download this repository into a local directory that will serve as your workspace root. All commands in this workspace assume they are run from this root directory.

```bash
git clone https://github.com/[repo-url] my-content-workspace
cd my-content-workspace
```

### Step 2 — Personalise AI-CONTEXT.md (the most important step)

Open `AI-CONTEXT.md` and fill in every section marked with a bracketed placeholder like `[YOUR NAME]` or `[YOUR POSITIONING STATEMENT]`. This file is the shared brain for both Claude Code and Gemini CLI — everything they produce will be shaped by what you write here. There are three sections that matter most.

**Workspace Identity** is where you define your positioning statement and your target audience. Be specific. "Senior Software Engineer" is too vague. "Infrastructure Engineer & Open-Source Contributor targeting Staff Engineer roles at developer-tools companies" gives the AI a concrete character to write as.

**The Rule of Three Content Pillars** is where you define the three topic areas your content will orbit. Each pillar should describe a cluster of related topics and name the capability that publishing in it demonstrates to your target audience. Think of each pillar as an answer to the question: "What should a recruiter or hiring manager conclude about me after reading five of my posts on this topic?"

**Persona & Tone** is where you describe how you want to sound. Write this as if you are briefing a ghostwriter. What would a senior practitioner in your field say that a junior person would not? What phrases or habits should be avoided? What experiences from your career should the AI reference when it strengthens a point?

### Step 3 — Review CLAUDE.md and GEMINI.md

In most cases you do not need to change these files — they contain role-specific wiring for each AI tool and default to sensible behaviour. Skim them to understand what each AI is being asked to do. The only section you might want to customise early on is the **CMS Schema** section in `CLAUDE.md`, if you are using a CMS other than Sanity.

### Step 4 — Verify your directory structure

The following directories must exist before you run any command. They ship with the repository as empty folders (tracked via `.gitkeep` files):

```
career/linkedin/
career/medium/
career/twitter/
career/website/
career/research/
```

The `career/research/` folder is particularly important. The pipeline saves all Gemini research outputs here after every research call, and these files accumulate into a research library that powers future sessions — a sequel article written three months from now can draw from research that was already run for a previous piece.

### Step 5 — Configure your CMS schema (if using the website feature)

If you are using the `/draft-website-json` command, place a sample JSON file in `career/website/` that matches your CMS schema exactly. The command reads an existing file before generating a new one to ensure it follows the same structure. If you are using Sanity with the default configuration, the schema is already defined in `AI-CONTEXT.md` and no additional setup is needed.

### Step 6 — Initialise both AI tools in the workspace (do this before your first content run)

This step is easy to skip and important not to. Both Claude Code and Gemini CLI use a workspace trust model: they only get access to the files in a directory after being explicitly opened there for the first time. If Gemini CLI has never been opened in this directory, Claude Code's subprocess calls to it during the research step will either fail silently or surface an interactive permission prompt in a context where you cannot respond to it. The fix is simple — you just need to open each tool in the workspace once, complete any prompts they present, then close them. After that, all future sessions work without interruption.

**Terminal 1 — Initialise Claude Code:**

Open a terminal, navigate to your workspace root, and start Claude Code:

```bash
cd path/to/my-content-workspace
claude
```

Claude Code will read `CLAUDE.md` automatically, which instructs it to read `AI-CONTEXT.md`. It may ask you to confirm it can access the workspace directory — confirm this. Once it loads and you see the prompt, you can type `exit` to close it. The workspace is now registered.

**Terminal 2 — Initialise Gemini CLI:**

Open a second terminal, navigate to the same workspace root, and start Gemini:

```bash
cd path/to/my-content-workspace
gemini
```

Gemini CLI will prompt you to authenticate via browser on first run and will ask for permission to read and write files in the current directory — grant this. It may also ask you to confirm which Google account to use if you have more than one. Once you see the Gemini prompt, type `exit` or press `Ctrl+C` to close it. The workspace is now registered for Gemini as well.

You only need to do this initialisation once per workspace. After both tools have been opened here at least once, you can run all subsequent sessions from Claude Code alone — Gemini will be invoked as a background subprocess without any further prompts.

**Running your first content session:**

Open Claude Code in the workspace root:

```bash
claude
```

Then run the master pipeline command with a topic of your choice:

```
/draft-master your topic or angle here
```

The pipeline will walk you through a series of checkpoints — category assignment, tag review, length selection, outline approval, and visual style choice — pausing at each one to collect your input before proceeding. You do not need to memorise the sequence; Claude Code will guide you through it.

### Step 7 — Iterate and build your content library

Each time you run `/draft-master`, the research output is saved to `career/research/`. When you run `/draft-calendar` to plan the next four weeks of content, Claude Code reads these research files and surfaces sequel opportunities — topics that already have research done and can be written without another Gemini call. Over time, your research library compounds: each article you publish seeds material for two or three future articles.

---

## How It Works

The pipeline is driven by eight slash commands that run inside Claude Code. Each command is defined as a Markdown file in `.claude/commands/` — Claude Code reads these files to know exactly how to execute each task, including which research to run, which checkpoints to pause at, and which files to create.

When you run `/draft-master <topic>`, the following sequence happens automatically, with pauses at the points marked as checkpoints.

Claude Code classifies your topic into one of your three content pillars and proposes a category from your approved categories list. It pauses and asks you to confirm the category before proceeding — this is a checkpoint because the category affects the website filter UI and must be deliberate.

Claude Code calls Gemini CLI via a bash subprocess with a structured research prompt. Gemini returns research in labelled sections (LANDSCAPE, DATA, FRAMEWORKS, CASE STUDIES, CONTRARIAN ANGLE, PRACTITIONER MISTAKES, and others). Claude Code saves this output to `career/research/YYYY-MM-DD_topic-slug-research.md` immediately. This file is the durable research record — all subsequent commands for the same topic draw from it rather than calling Gemini again.

Claude Code generates an ordered tag list from the research and shows it to you for review. This is a checkpoint because tag ordering affects SEO and platform discoverability — earlier tags carry more weight.

Claude Code assesses how much material the research contains relative to the target article length and presents three options: a standard 1,200–1,800 word article, a longer 2,000–2,500 word deep-dive, or a Part 1 now with a Part 2 planned for later. You choose. This is a checkpoint because article length affects which material gets included versus saved for sequels.

Claude Code builds the article outline following a structured template (opening hook, problem framing, named framework, real-world application, common mistakes, CTA) and shows it to you for approval. You can approve or request changes before any prose is written. This checkpoint can be skipped by adding "full draft" to your command.

With the outline approved, Claude Code writes the full article in Markdown, saving it to `career/medium/YYYY-MM-DD_topic-slug.md`. It then shows you the article and asks for any edits before generating the short-form content. This is a checkpoint because the LinkedIn post and Twitter thread are derived from the article — editing the article first prevents rework downstream.

Claude Code generates the image generation prompt for the article cover, shows it to you, and asks which visual style you want: lifelike, photo-realistic, illustration, or Ghibli. This is a checkpoint because the style choice is a creative decision.

Claude Code asks whether you also want a LinkedIn carousel and/or a Twitter image thread for this topic. If you confirm either, they are generated as additional pipeline steps using the same saved research.

Claude Code generates the LinkedIn feed post, the Twitter thread, and the CMS JSON, saving each to the correct folder with the matching date-slug prefix. It then outputs a publishing checklist with all file paths and a recommended publishing order.

---

## The Eight Slash Commands

All commands are run in the Claude Code terminal.

**`/draft-master <topic>`** runs the full pipeline. This is the command you will use most often. Add "full draft" to skip the outline approval checkpoint. Add "carousel" or "imagethread" to pre-confirm those optional outputs.

**`/draft-calendar`** generates or updates a rolling 4-week content calendar. It reads your existing research files to surface sequel opportunities that can be written without new research.

**`/draft-medium <topic>`** generates the long-form article as a standalone task, without producing the other formats.

**`/draft-linkedin <topic>`** generates the LinkedIn feed post only, reusing any existing research or article draft for the same topic.

**`/draft-twitter <topic>`** generates the Twitter/X thread only, reusing existing research where available.

**`/draft-website-json <topic>`** generates the CMS JSON portfolio piece, running a schema check against your existing files before generating.

**`/draft-carousel <topic>`** generates the LinkedIn carousel: a slide script, a rendered PDF, and the accompanying post text.

**`/draft-imagethread <topic>`** generates the Twitter image thread: tweet captions and AI image generation prompts for each card.

---

## Updating and Maintaining the Workspace

The maintenance model is designed around a single source of truth. When you want to update anything strategic — your positioning, your content pillars, your tone, the funnel architecture, any convention — edit only `AI-CONTEXT.md`. Both Claude Code and Gemini CLI read this file at the start of every session automatically, so your changes take effect immediately in the next session without any sync command.

When you want to add a new slash command, create a new Markdown file in `.claude/commands/` following the structure of the existing commands, then add a one-line description of it to the Slash Commands section of `CLAUDE.md`.

When you want to change how Claude Code specifically behaves — for example, changing the checkpoint protocol or the publishing order — edit `CLAUDE.md` only.

When you want to change how Gemini CLI specifically behaves — for example, changing the expected research output format — edit `GEMINI.md` only, and also update the corresponding `gemini -p "..."` prompt inside the relevant command file in `.claude/commands/`.

---

## File Naming Convention

Every file produced by this workspace uses a date-prefixed slug format: `YYYY-MM-DD_kebab-case-topic-slug`. For example, an article about north star metrics written on March 15, 2026 would be saved as `2026-03-15_north-star-metric-b2b-saas.md` in `career/medium/`, `2026-03-15_north-star-metric-b2b-saas-post.md` in `career/linkedin/`, `2026-03-15_north-star-metric-b2b-saas-thread.md` in `career/twitter/`, and `2026-03-15_north-star-metric-b2b-saas.json` in `career/website/`. The shared prefix makes it immediately obvious which files belong to the same publishing batch, regardless of which folder they are in.

---

## Contributing

This workspace is designed to be extended. New slash commands can be added by creating a Markdown file in `.claude/commands/` — the file is its own documentation and the structure of the existing commands serves as the template. If you build a command that others might find useful (for example, a command that generates YouTube scripts or podcast episode outlines from the same research), contributions are welcome via pull request.

When contributing, please follow the existing conventions: date-slug filenames, research preservation in `career/research/`, checkpoint pauses for decisions that require human judgment, and the single source of truth principle for `AI-CONTEXT.md`.

---

## Licence

MIT. See LICENCE file for details.