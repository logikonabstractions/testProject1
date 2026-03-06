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
- Define an initial architecture for a cloud-native web application that converts common text and geospatial file formats.

## Active assumptions / constraints
- The solution is cloud-native and browser-accessed.
- Supported conversions are limited to text and geospatial file families in scope.
- The architecture should remain implementation-agnostic (no specific products/vendors).

## Work log (current session)
- 2026-03-06: Created first architectural draft in `.architecture/ARCHITECTURE_DESCRIPTION.md` with four top-level components (10, 20, 30, 40) and system-wide concerns.
- 2026-03-06: Captured unresolved architecture decisions in `.architecture/PLAN.md` for review and input.

## Workflow state
<!-- Dispatcher flags. Checked = active/needed. Cleared once handled. -->
- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues
<!-- Keep only active issues here. Move resolved items to HISTORY.md. -->
- [ ] Arch.0.1: Identity and access model for initial release
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Confirm whether launch scope requires authenticated user accounts.
  - Notes: This impacts access boundaries, audit depth, and session lifecycle design.
