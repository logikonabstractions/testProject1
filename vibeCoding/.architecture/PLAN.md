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

### Arch-0.1 — Baseline access and retention policy model

- Type: DECISION
- Status: RESOLVED
- Related system / draft:
  - Cloud-native document conversion architecture (Arch.0.1)
- Why it matters:
  - Submission quotas, download sharing, and job-history retention strongly affect security boundaries, storage lifecycle, and user experience expectations.
- Known options / hypotheses:
  - Strict temporary model: anonymous-first, no sharing, short retention windows.
  - Hybrid model: optional accounts with higher quotas and limited-duration sharing links.
  - Account-centric model: authenticated usage required for persistent history and stronger access controls.
- Required input / evidence:
  - Received: users confirmed the service is public and unauthenticated.
  - Remaining: baseline retention/deletion window and link behavior tuning.
- Resolution criteria:
  - Decision on access model approved and reflected in architecture assumptions and component security considerations.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (Assumptions, Components 20/30/50, Open questions)
  - `.architecture/STATE.md` (Active issues)
- Notes:
  - Resolution: choose a public, anonymous access model with no account authentication.
  - Follow-up details (rate limits, expiration windows, link semantics) remain as open policy tuning items.
