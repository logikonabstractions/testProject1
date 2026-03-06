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
Define an MVP-friendly cloud-native architecture for browser-driven document and geospatial file conversion using microservice boundaries.

## Active assumptions / constraints
<!-- Keep only the assumptions or constraints that materially affect the current architecture draft. -->
- Cloud-native deployment context.
- Browser upload and download user journey.
- Microservice-oriented decomposition.
- Incremental MVP-first delivery.
- Media conversion (video/audio/image) remains out of scope.

## Work log (current session)
<!-- Append-only bullets for what changed and why. Prefer file/section references. -->
- 2026-03-06: Created first full architecture draft in `.architecture/ARCHITECTURE_DESCRIPTION.md` with six major components and system-wide concerns.
- 2026-03-06: Captured unresolved architecture decisions in `.architecture/PLAN.md` to prepare human review.

## Workflow state
<!-- Dispatcher flags. Checked = active/needed. Cleared once handled. -->
- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues
<!-- Keep only active issues here. Move resolved items to HISTORY.md. -->
- [x] Arch.0.1: Initial architecture baseline review
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human reviewer confirms open decisions and approves or requests updates.
  - Notes: Open decision items tracked as Arch-0.1 and Arch-0.2 in `.architecture/PLAN.md`.
