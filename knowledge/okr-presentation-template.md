# OKR Presentation Template

This file defines the slide structure used by the `okr-present` skill when generating the PPTX deck. Edit it to customise slide order, layout choices, or style guidance.

---

## Slide Order

1. Title
2. Objectives Overview
3. One slide per Objective (repeating)
4. Closing

---

## Slide Definitions

### Slide 1 — Title

| Field    | Value                 | PPTX Layout       |
|----------|-----------------------|-------------------|
| Title    | [Team Name] OKRs      | Title slide (0)   |
| Subtitle | [Quarter] [Year]      |                   |

---

### Slide 2 — Objectives Overview

| Field | Value                                              | PPTX Layout           |
|-------|----------------------------------------------------|-----------------------|
| Title | Our Objectives This Quarter                        | Title + Content (1)   |
| Body  | Bulleted list of all objective titles, one per OKR |                       |

---

### Slide 3+ — Objective Detail (one per OKR)

Repeat for each `okrs/okr-N.md` file.

| Field       | Value                                                         | PPTX Layout           |
|-------------|---------------------------------------------------------------|-----------------------|
| Title       | Objective title from `# OKR N:` heading                      | Title + Content (1)   |
| Objective   | Statement from `## Objective` section — bold                  |                       |
| Key Results | Numbered list from `## Key Results`, including CO-N links     |                       |
| Actions     | Bulleted list from `## Actions` section (omit if not present) |                       |

---

### Final Slide — Closing

| Field    | Value                          | PPTX Layout     |
|----------|--------------------------------|-----------------|
| Title    | Let's make it happen           | Title slide (0) |
| Subtitle | [Team Name] · [Quarter] [Year] |                 |

---

## Style Notes

- Title font size: 36pt
- Body font size: 18pt
- Keep each slide focused — one objective, its key results, and its actions only
- Key results must show their measurable target and CO-N reference
- If a slide has more than 4 key results, consider splitting the objective into two slides
- Output format: `.pptx` — compatible with PowerPoint, Keynote, and Google Slides
