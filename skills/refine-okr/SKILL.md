---
name: refine-okr
description: Reviews existing OKRs against common mistakes and best practices, reports findings by severity, and offers to fix flagged issues in place.
license: MIT
allowed-tools: "Read, Write, Bash, Grep"
metadata:
  author: ""
  version: "1.0.0"
  category: okr
---

# OKR Refine Skill

## Instructions

You are reviewing existing OKR files for quality issues and common pitfalls. Follow these steps precisely.

---

### Step 1 — Load context

1. List all files in `okrs/` matching `okr-*.md` and read each one. If none exist, tell the user to run the `elicit-okr` skill first and stop.
2. Read `knowledge/okr-requirements.md` for the team's constraints and type definitions.

---

### Step 2 — Review each OKR

For each OKR file, evaluate it against every check below. Record all findings before presenting anything.

---

#### Check 1 — Type classification ([ref](references/common-mistakes.md#1-misclassified-type))

- Is `**Type:**` set to `Committed`, `Aspirational`, or `Learning`? If missing, flag as **High**.
- Does the ambition level match the type?
  - **Committed**: must be achievable at 100%; requires resource commitment and schedule adjustment.
  - **Aspirational**: must feel genuinely uncomfortable; ~70% achievement is success.
  - **Learning**: framed around what the team wants to learn, not a fixed numeric outcome.
- Mismatches between stated type and actual target level are a **Medium** issue.

#### Check 2 — Sandbagging ([ref](references/sandbagging.md))

- Do committed OKRs credibly consume most of the team's available capacity?
- Do aspirational OKRs feel genuinely stretching, or just slightly above current practice?
- Red flags (flag **Medium**): target is only marginally above baseline; achievable without changing current practices; no resource pressure implied.

#### Check 3 — Business-as-usual ([ref](references/common-mistakes.md#2-business-as-usual-okrs))

- Would the team likely achieve this OKR without changing priorities?
- Does achieving it at 1.0 produce tangible end-user or economic value that wouldn't otherwise exist?
- If not, flag as **Medium**.

#### Check 4 — Objective quality ([ref](references/google-playbook.md))

- Is the objective an outcome or an activity? Activity-framed objectives (e.g. "Implement X", "Deploy Y") are **High** issues.
- Diagnostic: "If we achieve this, what gets better?" If the answer is unclear, the objective is too activity-focused.
- Does it deliver clear business or end-user value? Objectives with no identifiable benefit are **High**.

#### Check 5 — Key result quality ([ref](references/google-playbook.md#good-key-results))

- Does each KR include a specific numeric target and deadline? Missing metrics are **High**.
- Is each KR an outcome, not an activity? Flag activity language ("consult", "help", "analyze", "implement", "deliver") as **High**.
- **Sufficiency test**: would scoring 1.0 on every KR guarantee the objective is met? If doubt remains, the KRs are insufficient — flag **Medium**.

#### Check 6 — KPIs vs OKRs ([ref](references/kpis-vs-okrs.md))

- Are any KRs routine health metrics that belong on a standing dashboard rather than an OKR?
- Test: Is the team actively trying to move this metric this cycle, with a specific target and dedicated resources? If it's just being monitored, it's a KPI, not a KR — flag **Low**.

#### Check 7 — Initiatives quality

- Is each initiative concrete and specific? Vague initiatives ("improve the process") are **Low** issues.
- Is each initiative clearly linked to a specific KR it will advance? Unlinked initiatives are **Medium**.

---

### Step 3 — Present findings

Output one block per OKR:

```
## OKR N: <title> [<Type>]

### Issues
- [High] <finding> — <brief explanation>
- [Medium] <finding> — <brief explanation>
- [Low] <finding> — <brief explanation>

### Suggestions
- <specific actionable improvement>
```

**Severity guide:**
- **High** — OKR is broken or meaningless without this fix (activity-based KRs, no metric, missing type, no business value)
- **Medium** — quality is degraded but the OKR functions (sandbagging, timid aspirational, insufficient KRs, unlinked initiatives)
- **Low** — polish and clarity (KPI confusion, vague initiatives, wording)

If an OKR has no issues, state that explicitly.

After all OKRs, print a summary count: total issues by severity.

---

### Step 4 — Offer to fix

Ask the user:
> "Would you like to fix any of the flagged OKRs now, or is this review informational?"

If the user wants to fix specific OKRs:
- Work through each flagged section (objective, type, KRs, initiatives) one at a time.
- Propose the corrected wording and confirm with the user before writing.
- Overwrite the relevant `okrs/okr-N.md` using the same format as `elicit-okr` Step 5.
- Tell the user the file has been saved after each fix.
