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
Design a cloud-native architecture for browser-based document and geospatial file conversion with durable job tracking and secure output delivery.

## Active assumptions / constraints
- Architecture remains implementation-agnostic with no concrete vendor/product choices.
- Supported conversion scope excludes video, image, and audio/media formats.
- Users submit and retrieve files through browser-driven interactions.

## Work log (current session)
- 2026-03-06: Created first architecture draft in `.architecture/ARCHITECTURE_DESCRIPTION.md` with components, interactions, and system-wide concerns.
- 2026-03-06: Captured open architecture decisions in `.architecture/PLAN.md` for review.

## Workflow state
<!-- Dispatcher flags. Checked = active/needed. Cleared once handled. -->
- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues
<!-- Keep only active issues here. Move resolved items to HISTORY.md. -->
- [ ] Arch.0.1: Validate operational policy defaults
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human reviewer confirms upload limits, completion mode, and default retention policy.
  - Notes: Open questions are listed in `.architecture/PLAN.md` and the architecture draft.
