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
Draft a cloud-native architecture for browser-driven document conversion with micro-service boundaries and MVP-first evolution.

## Active assumptions / constraints
- Browser-based upload and download user flow is the only client channel for MVP.
- Scope excludes media conversions (video, audio, images).
- Architecture must remain technology-agnostic at component definition level.
- Output artifacts are temporary and should be lifecycle-managed.

## Work log (current session)
- 2026-03-06: Completed first full architectural draft in `.architecture/ARCHITECTURE_DESCRIPTION.md` with component set 10–50, interactions, system-wide concerns, and open questions.
- 2026-03-06: Marked draft as awaiting human review before promoting status to DONE.

## Workflow state
<!-- Dispatcher flags. Checked = active/needed. Cleared once handled. -->
- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues
<!-- Keep only active issues here. Move resolved items to HISTORY.md. -->
- [ ] Arch.0.1: Confirm MVP constraints and access model
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human reviewer confirms authentication stance, max file limits, and retention expectations for MVP.
  - Notes: Open questions are tracked in `.architecture/ARCHITECTURE_DESCRIPTION.md` and `.architecture/PLAN.md`.
