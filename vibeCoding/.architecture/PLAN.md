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

### Arch-0.1 — Identity requirement for conversion requests

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Arch.0.1
- Why it matters:
  - Authentication posture determines trust boundaries, abuse controls, and user ownership model for artifacts.
- Known options / hypotheses:
  - Require authenticated users for all conversions.
  - Allow anonymous conversions with stricter size/rate limits.
  - Support both modes with policy-based gating.
- Required input / evidence:
  - Product decision on user onboarding friction versus abuse risk tolerance.
- Resolution criteria:
  - Explicit policy for who can submit requests and retrieve results.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 10, 20, 60; system-wide security concerns)
- Notes:
  - Current draft assumes authentication is available but not mandated.

### Arch-0.2 — File retention and deletion policy

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Arch.0.1
- Why it matters:
  - Retention windows impact storage cost, compliance exposure, and user experience for delayed downloads.
- Known options / hypotheses:
  - Short retention with mandatory immediate download.
  - Configurable retention by service tier.
  - User-controlled deletion with hard maximum retention.
- Required input / evidence:
  - Business and compliance requirements for stored customer files.
- Resolution criteria:
  - Defined default retention, max retention, and deletion guarantees.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (component 50; compliance and reliability concerns)
- Notes:
  - Current draft marks retention as a system-wide concern without fixed thresholds.

### Arch-0.3 — Service envelope for workload limits

- Type: CLARIFICATION
- Status: OPEN
- Related system / draft:
  - Arch.0.1
- Why it matters:
  - Max file size, expected throughput, and duration targets shape queueing, scaling, and SLA design.
- Known options / hypotheses:
  - Interactive-first envelope with lower file-size limits.
  - Batch-friendly envelope with longer processing windows.
- Required input / evidence:
  - Product-level SLO expectations and anticipated usage profile.
- Resolution criteria:
  - Documented upper bounds for accepted file size and target completion profile.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 30, 40, 50; performance and reliability concerns)
- Notes:
  - This clarification can be resolved before any component-level deep dive.
