# OKR Requirements & Constraints

## Quantity Constraints

- **Max objectives per team per cycle**: 5
- **Min objectives per team per cycle**: 1
- **Key results per objective**: 2–4

## Quality Constraints

- Each key result must include a measurable metric or quantified target (a number, percentage, threshold, or binary milestone with a deadline)
- Each key result must be traceable to at least one company OKR — reference the company objective using CO-N notation (e.g. "links to CO-2")
- Objectives must describe outcomes the team is trying to achieve, not activities or deliverables
- Key results must measure outcomes, not effort or output (avoid "we will ship X"; prefer "X metric improves to Y")

## Actions

- include_actions: true
- **Actions per key result**: 1–3 concrete steps that directly drive the key result
- Actions should be specific and realistic given the team's delivery environment
- Actions must be clearly linked to the key result they support

## Output Format

- Each OKR is saved as a separate file: `okrs/okr-N.md` (e.g. `okrs/okr-1.md`, `okrs/okr-2.md`)
- Required sections: `## Objective`, `## Key Results`
- Required when include_actions is true: `## Actions`

## Compliance Check

An existing OKR file is considered valid (and will not be re-elicited) if it contains:
- A non-empty `## Objective` section with at least one line of content after the heading
- At least 2 numbered items listed under `## Key Results`
