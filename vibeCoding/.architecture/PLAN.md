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

### Arch-0.1 — MVP identity and completion signaling strategy

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document conversion architecture (Arch.0.1)
- Why it matters:
  - Identity posture and completion signaling influence trust boundaries, API complexity, and user experience for the first release.
- Known options / hypotheses:
  - Option A: authenticated accounts required, polling-only completion status.
  - Option B: anonymous conversions with temporary tokenized access, polling-only completion status.
  - Option C: authenticated accounts plus push-based completion signaling.
- Required input / evidence:
  - Product direction on friction tolerance for first-time users and expected conversion volume/latency.
- Resolution criteria:
  - A single MVP option is selected and reflected in components 10, 20, and 80.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 10, 20, 80; open questions)
- Notes:
  - Decision can be revisited after MVP telemetry, but one baseline is needed for implementation planning.
