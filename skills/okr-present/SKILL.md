---
name: okr-present
description: Generates a PPTX slide deck from okrs/okr-N.md files and saves it to presentations/. Title slide includes team name, quarter, and year.
license: MIT
allowed-tools: "Read, Write, Bash"
metadata:
  author: ""
  version: "1.0.0"
  category: okr
---

# OKR Present Skill

## Instructions

You are generating an OKR PPTX presentation from saved OKR files. Follow these steps precisely.

---

### Step 1 — Verify OKR files exist

1. Attempt to read `okrs/okr-1.md`. If the file does not exist, tell the user to run the `okr-elicit` skill first and stop.
2. Read all available `okrs/okr-N.md` files (increment N until a file is not found). Collect them all.
3. For each file, confirm it contains a `## Objective` section and at least one `## Key Results` item. Warn about any incomplete files but continue with the valid ones.

---

### Step 2 — Gather presentation metadata

Ask the user for three things in a single message:

1. **Team name** — the name of the team this presentation is for
2. **Quarter** — Q1, Q2, Q3, or Q4
3. **Year** — the calendar year (e.g. 2025)

Wait for the user's response before proceeding.

---

### Step 3 — Load the slide template

Read `knowledge/okr-presentation-template.md`. Use it as the structural guide for slide order, layout choices, and style notes. If the file is missing, use the default structure defined in Step 4.

---

### Step 4 — Build the presentation

First, ensure python-pptx is available:

```bash
pip install python-pptx --quiet 2>&1 | tail -1
```

Then write a Python script to `presentations/_build_okr.py` that creates the PPTX using the content from the OKR files and the metadata from Step 2. The script must:

**Slide 1 — Title**
- Title placeholder: `[Team Name] OKRs`
- Subtitle placeholder: `[Quarter] [Year]`

**Slide 2 — Objectives Overview**
- Title: `Our Objectives This Quarter`
- Body: bulleted list of all objective titles (one per OKR file)

**Slides 3 to N+2 — One slide per Objective**

For each OKR file, add one slide with:
- Title: the objective title extracted from the `# OKR N:` heading line
- Body content in this order:
  1. Objective statement (from `## Objective` section) — bold
  2. Blank line
  3. `Key Results` sub-heading, then numbered list of KRs (from `## Key Results`), each on its own line including the CO-N reference
  4. If the file has an `## Actions` section: `Actions` sub-heading, then bulleted list of actions

**Slide N+3 — Closing**
- Title: `Let's make it happen`
- Subtitle: `[Team Name] · [Quarter] [Year]`

Use the `LAYOUT_TITLE = 0` (title slide) layout for slides 1 and the closing slide, and `LAYOUT_TITLE_CONTENT = 1` (title and content) for all other slides. Use `pptx.util.Pt` for font sizes: 36pt for slide titles, 18pt for body text.

Output filename:
```
presentations/okr-[Q][Year]-[team-name-lowercase-hyphenated].pptx
```
Example: `presentations/okr-Q2-2025-platform-team.pptx`

Create the `presentations/` directory if it does not exist.

---

### Step 5 — Execute and verify

Run the script:

```bash
python presentations/_build_okr.py
```

Check that the output file exists and is non-empty. If the script errors, fix the error and re-run. Remove the temporary build script after a successful run:

```bash
rm presentations/_build_okr.py
```

---

### Step 6 — Confirm completion

Tell the user:
- The path to the saved `.pptx` file
- That they can open it directly in PowerPoint, Keynote, or Google Slides
- That they can run this skill again after updating OKR files to regenerate the deck
