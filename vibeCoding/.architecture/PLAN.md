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

### Arch-0.1 — Conversion admission-control limits

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document-conversion architecture (Arch.0.1)
- Why it matters:
  - Upload size and concurrency limits shape gateway validation, queue pressure, and user experience.
- Known options / hypotheses:
  - Conservative default limits with explicit expansion path.
  - Tiered limits by user class.
- Required input / evidence:
  - Expected usage profile and acceptable processing-time targets.
- Resolution criteria:
  - Explicitly defined maximum upload size and concurrent jobs per user/session.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 20, 40; open questions)
- Notes:
  - Pending human decision.

### Arch-0.2 — Completion model for short-running conversions

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document-conversion architecture (Arch.0.1)
- Why it matters:
  - Completion model affects user responsiveness and API orchestration complexity.
- Known options / hypotheses:
  - Fully asynchronous completion for all conversions.
  - Hybrid model allowing bounded synchronous completion for small jobs.
- Required input / evidence:
  - Product preference for UX simplicity versus reduced waiting hops.
- Resolution criteria:
  - Chosen default completion behavior and criteria for alternate path, if any.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 10, 20, 40; open questions)
- Notes:
  - Pending human decision.

### Arch-0.3 — Default artifact retention policy

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document-conversion architecture (Arch.0.1)
- Why it matters:
  - Retention period drives storage lifecycle design, governance expectations, and user trust.
- Known options / hypotheses:
  - Fixed default retention window.
  - Configurable retention within bounded policy limits.
- Required input / evidence:
  - Compliance expectations and operational storage constraints.
- Resolution criteria:
  - Documented default retention period and override policy.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 30, 50; open questions)
- Notes:
  - Pending human decision.
