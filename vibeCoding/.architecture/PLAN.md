# PLAN

## How to use this file

- This is the **architecture discussion and investigation backlog**.
- It is **not** an implementation checkpoint plan.
- Use it to track architecture questions that require clarification, comparison, investigation, or explicit decision.
- Keep one item per question or decision.
- When a question is resolved, keep the item here for traceability, mark it `RESOLVED`, and summarize the outcome in `HISTORY.md`.

## Item format

Each item should contain:

- Type
- Status
- Why it matters
- Known options / hypotheses
- What input or evidence is needed
- Resolution criteria
- Links to affected architecture drafts or sections

## Item types

- `CLARIFICATION` — the problem statement is missing key information
- `DECISION` — multiple valid architectural directions exist and a choice is needed
- `INVESTIGATION` — more analysis is needed before choosing a direction
- `ASSUMPTION_VALIDATION` — an assumption must be confirmed before the architecture can stabilize
- `RISK_REVIEW` — a non-functional or cross-cutting concern needs explicit review

## Item statuses

- `OPEN`
- `IN_PROGRESS`
- `BLOCKED`
- `DECISION_REQUIRED`
- `RESOLVED`

## Active architecture questions

### Arch-0.0 — <short title>

- Type: <CLARIFICATION | DECISION | INVESTIGATION | ASSUMPTION_VALIDATION | RISK_REVIEW>
- Status: <OPEN | IN_PROGRESS | BLOCKED | DECISION_REQUIRED | RESOLVED>
- Related system / draft:
  - <system name or architecture draft identifier>
- Why it matters:
  - <why this question materially affects the architecture>
- Known options / hypotheses:
  - <option or hypothesis>
- Required input / evidence:
  - <what information, analysis, or human decision is needed>
- Resolution criteria:
  - <what must be true for this item to be considered resolved>
- Affected sections:
  - <component ids / architecture sections / document paths>
- Notes:
  - <optional>
