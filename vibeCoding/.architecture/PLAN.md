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

### Arch-0.1 — Launch user access mode

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document conversion architecture (Arch.0.1)
- Why it matters:
  - The launch access model determines identity complexity, authorization policy depth, and user experience flows.
- Known options / hypotheses:
  - Anonymous-only launch with lightweight abuse controls.
  - Authenticated-only launch with user-scoped job history.
  - Mixed mode where anonymous is allowed with stricter limits.
- Required input / evidence:
  - Product decision on expected user lifecycle and abuse tolerance.
- Resolution criteria:
  - A single launch access model is selected and reflected in components 10, 20, and 60.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 10, 20, 60; system-wide security concerns)
  - `.architecture/STATE.md` (active issue Arch.0.1)
- Notes:
  - Decision can be revisited for later revisions but must be explicit for Arch.0.1 completion.

### Arch-0.2 — Conversion fidelity targets by format family

- Type: CLARIFICATION
- Status: OPEN
- Related system / draft:
  - Cloud-native document conversion architecture (Arch.0.1)
- Why it matters:
  - Fidelity expectations influence pipeline complexity, validation responsibilities, and error-handling semantics.
- Known options / hypotheses:
  - Best-effort conversion for all formats.
  - Strict fidelity targets for selected business-critical format pairs.
  - Tiered approach with documented quality classes.
- Required input / evidence:
  - Product quality requirements or acceptance criteria per format family.
- Resolution criteria:
  - At least one explicit fidelity policy is adopted and reflected in component 30 responsibilities.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (component 30 and open questions)
- Notes:
  - This is a clarifying requirement rather than a hard blocker for review.
