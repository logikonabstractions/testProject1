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

### Arch-0.1 — Ordering and dispatch guarantees for conversion workload

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Arch.0.1
- Why it matters:
  - Dispatch semantics influence throughput, fairness, and predictability for user-visible completion times.
- Known options / hypotheses:
  - Strict ordering by user/session job stream.
  - Best-effort parallel dispatch with idempotent completion handling.
  - Hybrid policy (ordered within a narrow scope, parallel globally).
- Required input / evidence:
  - Product expectation on UX predictability versus raw throughput for MVP.
- Resolution criteria:
  - Clear rule selected for dispatch/ordering guarantees and reflected in component interaction constraints.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (Components 20, 30, 50; open questions)
- Notes:
  - Decision can remain provisional for MVP but must be explicit.

### Arch-0.2 — Access model for MVP (anonymous vs authenticated)

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Arch.0.1
- Why it matters:
  - Authentication requirements materially change security boundaries, retention risk, and abuse controls.
- Known options / hypotheses:
  - Anonymous conversion with strict rate and retention limits.
  - Mandatory authenticated access from day one.
  - Mixed model: anonymous trial with authenticated higher limits.
- Required input / evidence:
  - Product and compliance expectations for user identity, quota management, and auditability.
- Resolution criteria:
  - MVP access model chosen and translated into explicit constraints for components 10, 20, and 60.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (Components 10, 20, 60; system-wide concerns)
- Notes:
  - Closely related to retention and policy governance requirements.
