---
name: elicit-okr
description: Interactively elicits team-level OKRs (Objectives, Key Results, and Actions) aligned to company strategy, then saves each one to okrs/okr-N.md. Skips if valid OKR files already exist.
license: MIT
allowed-tools: "Read, Write, Grep"
metadata:
  author: ""
  version: "1.0.0"
  category: okr
---

# OKR Elicit Skill

## Instructions

You are facilitating an OKR elicitation session. Follow these steps precisely.

---

### Step 1 — Check for existing valid OKRs

Before asking the user anything, scan for existing OKR files:

1. List all files in the `okrs/` directory and identify those matching the `okr-*.md` pattern.
2. For each file found, check that it contains:
   - A non-empty `## Objective` section (at least one line of content after the heading)
   - At least 2 numbered items under `## Key Results`
3. Read `knowledge/okr-requirements.md` to find the configured maximum number of objectives.
4. If the number of valid OKR files reaches the configured maximum, print a summary and stop. If valid files exist but haven't reached the maximum, show the summary and ask the user if they want to continue defining more OKRs or edit existing ones.

If any OKR file is missing or invalid (missing Objective, fewer than 2 Key Results), proceed with elicitation for the incomplete ones only.

---

### Step 2 — Load knowledge context

Read both knowledge files before starting any conversation with the user:

- `knowledge/company-okrs.md` — company-level OKRs and strategic business context
- `knowledge/okr-requirements.md` — constraints governing number, quality, and format of team OKRs

Extract and hold in mind:
- The list of company objectives (CO-1, CO-2, …) and their key results
- The maximum number of team objectives allowed (default: 3–5)
- The required number of key results per objective (default: 2–4)
- Whether actions are enabled (`include_actions: true`)
- The number of actions per key result when enabled (default: 1–3)

If either knowledge file is missing or still contains unfilled template markers (e.g., `<Brief description...>` or `CO-1: <...>`), warn the user that the knowledge files need to be filled in before proceeding, and stop.

---

### Step 3 — Explain the session to the user

Briefly introduce what you are doing:
- How many objectives you will work through together
- What company OKRs you are aligning to
- That you will guide them through objectives → key results → actions

Ask how many team objectives they want to define this cycle (within the configured min/max range).

---

### Step 4 — Elicit each objective

For each objective (numbered 1 to N, where N is the user's chosen count):

**4a. Propose or accept an objective**
- Ask the user to state a proposed objective, or offer to suggest one based on the company OKRs.
- Validate the objective is:
  - Clear and meaningful (describes what the team is trying to achieve, not how)
  - Traceable to at least one company objective — ask the user which CO-N it supports if not obvious
  - Appropriately scoped for a single team in one cycle
- If the objective is weak or vague, suggest a sharper version and ask the user to confirm or adjust.
- Confirm the final objective wording with the user before proceeding.

**4b. Elicit key results for this objective**
- Tell the user you need 2–4 measurable key results for this objective.
- For each key result:
  - Ask the user to propose one, or offer a suggestion grounded in the company OKRs and the objective.
  - Validate the KR:
    - Contains a specific metric or quantified target (e.g., a number, percentage, or threshold)
    - Is an outcome, not an activity (avoid "we will do X"; prefer "X increases to Y by Z")
    - Links to a specific company OKR (note which CO-N it supports)
  - If the KR is vague or unmeasurable, suggest a stronger version and confirm with the user.
  - Record the confirmed KR with its CO-N reference.
- Stop when the user has confirmed 2–4 key results.

**4c. Elicit actions (only if `include_actions: true` in requirements)**
- For each confirmed key result, ask the user for 1–3 concrete actions that will directly move that KR.
- Actions must be specific, realistic, and clearly linked to their KR.
- Suggest actions if the user needs help, drawing on the business context.
- Confirm each action with the user.

---

### Step 5 — Save the OKR file

After completing elicitation for each objective, immediately write it to `okrs/okr-N.md` (where N matches the objective number). The `okrs/` directory already exists via `.gitkeep`.

Use exactly this format:

```
# OKR N: <Objective Title>

## Objective
<Objective statement — the confirmed wording from Step 4a>

## Key Results
1. <KR1 — measurable outcome (links to CO-X)>
2. <KR2 — measurable outcome (links to CO-X)>
3. <KR3 — measurable outcome (links to CO-X)>

## Actions
- <Action 1 — drives KR1>
- <Action 2 — drives KR2>
- <Action 3 — drives KR3>
```

Omit the `## Actions` section entirely if `include_actions` is false or not set in the requirements.

Tell the user the file has been saved and show them the path.

---

### Step 6 — Confirm completion

After all OKRs are saved, print a concise summary:

```
OKR elicitation complete. Files written:
- okrs/okr-1.md — <Objective 1 title>
- okrs/okr-2.md — <Objective 2 title>
...
```

Remind the user to fill in `knowledge/company-okrs.md` with real company OKR content if they used placeholder data.
