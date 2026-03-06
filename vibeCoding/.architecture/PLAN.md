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

### Arch-0.1 — MVP access model and usage limits

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Document conversion architecture draft Arch.0.1
- Why it matters:
  - Authentication policy and file-size/throughput limits shape API boundary controls, abuse protections, and storage lifecycle behavior.
- Known options / hypotheses:
  - Authenticated-only MVP with per-user quotas.
  - Mixed anonymous + authenticated model with stricter anonymous limits.
- Required input / evidence:
  - Product direction on user onboarding friction vs abuse risk tolerance.
  - Expected traffic profile and typical file sizes for early users.
- Resolution criteria:
  - A confirmed MVP policy for authentication requirements and hard usage limits.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 10, 20, 30, 50; system-wide concerns)
- Notes:
  - Decision can remain provisional if clearly time-boxed to MVP.

### Arch-0.2 — Conversion capability prioritization

- Type: CLARIFICATION
- Status: OPEN
- Related system / draft:
  - Document conversion architecture draft Arch.0.1
- Why it matters:
  - The initial set of format pairs determines early conversion domain complexity and validation responsibilities.
- Known options / hypotheses:
  - Start with high-frequency text conversions only.
  - Include one geospatial conversion path in MVP to validate multi-domain architecture.
- Required input / evidence:
  - Product ranking of most critical conversion pairs.
  - Any known compliance/quality constraints by format family.
- Resolution criteria:
  - MVP conversion matrix approved for first release scope.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (component 40, interaction summary, open questions)
- Notes:
  - Prioritization does not change macro-architecture but affects rollout sequencing.
