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

### Arch-0.1 — Initial identity and access posture

- Type: DECISION
- Status: DECISION_REQUIRED
- Related system / draft:
  - Cloud-native document conversion architecture (Arch.0.1)
- Why it matters:
  - Identity scope affects trust boundaries, artifact isolation, access token lifetime, and audit requirements across the entire architecture.
- Known options / hypotheses:
  - Authenticated-user model from launch.
  - Anonymous session model with short-lived scoped access.
  - Hybrid model supporting both anonymous and authenticated flows.
- Required input / evidence:
  - Product decision on launch requirements for user accounts and expected usage pattern.
- Resolution criteria:
  - A confirmed launch posture is selected and reflected in component security notes.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 10, 20, 30; system-wide security)
  - `.architecture/STATE.md` active issues
- Notes:
  - Decision should be made before finalizing architecture status as `DONE`.

### Arch-0.2 — Capacity assumptions for queueing and processing model

- Type: ASSUMPTION_VALIDATION
- Status: OPEN
- Related system / draft:
  - Cloud-native document conversion architecture (Arch.0.1)
- Why it matters:
  - Throughput and file-size expectations shape control-plane limits, asynchronous backlog handling, and processor scaling policy.
- Known options / hypotheses:
  - Low-volume interactive usage with small files.
  - Mixed volume including occasional large files.
  - Sustained high volume requiring aggressive horizontal scaling.
- Required input / evidence:
  - Target file-size limits and expected daily/peak conversion volume.
- Resolution criteria:
  - Initial volume and size assumptions are documented and accepted for architecture baseline.
- Affected sections:
  - `.architecture/ARCHITECTURE_DESCRIPTION.md` (components 20, 30, 40; performance and reliability concerns)
- Notes:
  - This can remain an explicit assumption for initial draft review if product data is not yet available.
