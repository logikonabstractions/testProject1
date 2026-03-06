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

### Arch-0.1 — Processing interaction model

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document-conversion architecture (Arch.0.1)
- Why it matters:
  - Determines whether users always receive deferred job handling or can receive immediate results for small/quick conversions.
- Known options / hypotheses:
  - Fully asynchronous conversion flow for all requests.
  - Hybrid flow: synchronous fast path under defined thresholds plus asynchronous fallback.
- Required input / evidence:
  - Product preference for UX responsiveness vs consistency and operational simplicity.
- Resolution criteria:
  - A single default processing model is selected and accepted for the architecture baseline.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` components 10, 20, 30.
- Notes:
  - Choice affects client UX and orchestration complexity.

### Arch-0.2 — User access posture

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document-conversion architecture (Arch.0.1)
- Why it matters:
  - Identity requirements shape security boundaries, abuse controls, and audit obligations.
- Known options / hypotheses:
  - Authenticated users only.
  - Anonymous conversion allowed with stricter rate/size limits.
  - Mixed model with optional accounts.
- Required input / evidence:
  - Product and governance preference on friction, accountability, and abuse tolerance.
- Resolution criteria:
  - Accepted access posture with explicit guardrails.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` components 10, 20, 40, 50.
- Notes:
  - Also influences incident response and data-retention policies.

### Arch-0.3 — File retention policy baseline

- Type: CLARIFICATION
- Status: OPEN
- Related system / draft:
  - Cloud-native document-conversion architecture (Arch.0.1)
- Why it matters:
  - Retention duration influences privacy risk, storage cost, and user retrieval expectations.
- Known options / hypotheses:
  - Immediate deletion after successful download.
  - Short fixed retention window.
  - Configurable retention by user tier.
- Required input / evidence:
  - Product policy and legal/compliance constraints.
- Resolution criteria:
  - Baseline retention rule and deletion behavior approved.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` components 20 and 40, system-wide governance concerns.
- Notes:
  - Must be aligned with audit-trail retention requirements.
