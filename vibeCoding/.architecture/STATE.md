# STATE

This file keeps track of architectural discussions. Mostly when tricker issues needs sorting with back & forth, or when multiple approaches would meet the objectives and the agent prefers to obtain input. 

## Session read order

1. `AGENTS.md` (optional if already read this session)
2. `.architecture/AGENTS_ARCHITECTURE.md`
3. `.architecture/STATE.md` (this file)
4. `.architecture/ARCHITECTURE_DESCRIPTION.md`
5. `.architecture/HISTORY.md` (optional)

## State management rules

- The current target system should remain stable during a draft unless a human changes the problem statement or scope.
- The status can be set to `DONE` only when the human reviewer has explicitely approved the result
- Keep this file focused on current execution state. Put rollups and resolved items in `HISTORY.md`.

## Current focus

- Revision ID: Arch.0.1
- Status: IN_REVIEW  <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->

## Objective (current draft)
Produce an initial architecture draft for a cloud-native web document-conversion system covering major components, interfaces, and cross-cutting concerns.

## Active assumptions / constraints

- The architecture remains implementation-agnostic and avoids naming specific products.
- Conversion scope includes common text and geo formats only.
- Upload and download are browser-mediated user interactions.

## Work log (current session)

- 2026-03-06: Created first complete architectural component draft in `.architecture/ARCHITECTURE_DESCRIPTION.md` based on the provided problem statement.
- 2026-03-06: Raised unresolved architectural decision items in `.architecture/PLAN.md` for workflow mode, identity model, and retention policy.

## Workflow state

- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues

- [ ] Arch.0.1: Processing model decision (synchronous vs asynchronous fast path)
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human reviewer selects preferred processing interaction model.
  - Notes: Impacts orchestration interface design, user status UX, and scalability behavior.
- [ ] Arch.0.2: Access model decision (authenticated-only vs anonymous allowed)
  - Impact: MAJOR <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human reviewer confirms required identity and access posture.
  - Notes: Directly affects security boundary and auditability requirements.
