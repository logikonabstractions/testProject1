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

### Arch-0.1 — MVP identity requirement model

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document conversion platform (Arch.0.1)
- Why it matters:
  - Identity posture defines access boundaries for upload/download flows and affects auditability expectations.
- Known options / hypotheses:
  - Allow anonymous conversions for MVP with scoped short-lived download access.
  - Require authenticated users for all conversions from first release.
- Required input / evidence:
  - Product and compliance direction on acceptable exposure and traceability requirements.
- Resolution criteria:
  - A single access model is selected and accepted by reviewer.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` components 20, 50, 60 and system-wide security concerns.
- Notes:
  - Decision has direct impact on authorization and access-log requirements.

### Arch-0.2 — Artifact retention and deletion baseline

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document conversion platform (Arch.0.1)
- Why it matters:
  - Retention policy controls storage costs, compliance posture, and user expectations for download availability.
- Known options / hypotheses:
  - Very short retention window oriented to transient conversions.
  - Configurable retention tiers based on account or request profile.
- Required input / evidence:
  - Product requirements for user convenience and compliance constraints for data minimization.
- Resolution criteria:
  - Default retention window and deletion strategy are explicitly approved.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` component 50 and compliance/reliability sections.
- Notes:
  - This decision should also define whether manual early deletion is required in MVP.
