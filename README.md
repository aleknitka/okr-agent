# okr-agent

`okr-agent` helps teams turn company strategy into clearer team-level OKRs. It uses company OKRs, business context, and delivery constraints to propose objectives, key results, and initiatives that are aligned with business aims and practical to execute.

## What OKRs Are

OKRs are a way to connect strategy to execution.

- Objectives describe what a team is trying to achieve.
- Key results define how success will be measured.
- Initiatives are the concrete steps the team takes to move those key results.

> We will **[Objective]** as measured by **[Key Results]** via **[Initiatives]**.

Good OKRs create a clear link between business priorities and day-to-day work.

## OKR Types

Every OKR belongs to one of three types:

- **Committed** — must be fully achieved by the end of the cycle. Resources and schedules are adjusted to ensure 100% completion. Failing a committed OKR is a serious signal.
- **Aspirational** — a stretch goal designed to push the team further than comfortable execution allows. ~70% achievement is considered a success. These can carry forward across cycles.
- **Learning** — used when there is genuine uncertainty about what is possible or what approach works. The goal is framed around what the team wants to learn rather than a specific outcome to commit to.

Mixing all three types across a team's OKRs is normal. The type signals to the rest of the organisation how to interpret progress against the goal.

## What Good OKRs Look Like

Strong objectives are clear, meaningful, and directly connected to business value.

Strong key results are specific, measurable, and focused on outcomes rather than activity.

Strong initiatives are concrete, realistic, and shaped by the team's actual delivery environment, including tools, platforms, technical methods, and operating constraints.

## How The Agent Helps

Teams can use this agent with their company OKRs and other relevant context to work out better team-level OKRs.

The agent helps by:

- placing proposed OKRs in the context of business value and strategic aims
- improving the clarity of objectives without making them overly vague or overly detailed
- refining key results so they are measurable and useful for decision-making
- translating delivery constraints such as tech stack, platforms, tools, and methods into more realistic initiatives
- helping teams define initiatives that drive the key results needed to achieve objectives

## Skills

The agent provides three skills designed to be run in order.

### 1. `elicit-okr`
Guides you through a structured conversation to define team-level OKRs aligned to company strategy. Saves each OKR to `okrs/okr-N.md`. Skips OKRs that are already complete so you can run it incrementally.

### 2. `refine-okr`
Reviews all saved OKRs against common mistakes and best practices — including type classification, sandbagging, activity-framed objectives, and insufficient key results. Reports issues by severity and offers to fix flagged OKRs in place.

### 3. `present-okr`
Generates a PPTX slide deck from the saved OKR files. Produces one slide per OKR showing the type, objective, key results, and initiatives, plus a title slide and a closing slide.

## Suggested Team Workflow

1. Fill in `knowledge/company-okrs.md` with your company OKRs and supporting business context.
2. Fill in `knowledge/okr-requirements.md` with your team's constraints — max objectives, key results per objective, and any context specific to your delivery environment.
3. Run `elicit-okr` to define your team OKRs through a guided conversation.
4. Run `refine-okr` to review the OKRs for common mistakes and improve them before sharing.
5. Run `present-okr` to generate a PPTX deck ready for stakeholder review.
