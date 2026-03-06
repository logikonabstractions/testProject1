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
Create a first-pass architecture draft for a cloud-native document conversion system covering text and geo file types.

## Active assumptions / constraints
- The architecture must avoid concrete technology or vendor choices.
- End users interact only through a web browser flow.
- Media conversion use cases (video/audio/images) remain out of scope.

## Work log (current session)
- 2026-03-06: Produced initial architecture component draft in `.architecture/ARCHITECTURE_DESCRIPTION.md`, including system-wide concerns and open questions for review.
- 2026-03-06: Updated workflow flags and active issue state to request human review on unresolved policy and retention decisions.

## Workflow state
- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues
- [x] Arch.0.1: Baseline policy and retention decisions required
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human confirms quota model, sharing posture, and history retention expectations.
  - Notes: Tracked in open questions and PLAN item Arch-0.1.
