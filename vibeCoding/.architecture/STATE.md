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
Design a cloud-native architecture for browser-driven document conversion across text and geospatial formats with asynchronous processing and secure result retrieval.

## Active assumptions / constraints
<!-- Keep only the assumptions or constraints that materially affect the current architecture draft. -->
- Cloud-hosted deployment and browser-first interaction model.
- Media conversion (audio/video/image) remains out of scope.
- Architecture must stay technology-agnostic and role-based.

## Work log (current session)
<!-- Append-only bullets for what changed and why. Prefer file/section references. -->
- 2026-03-06: Drafted initial architecture components and end-to-end interaction model in `.architecture/ARCHITECTURE_DESCRIPTION.md`.
- 2026-03-06: Added open architectural questions and moved status to `IN_REVIEW` pending human feedback.

## Workflow state
<!-- Dispatcher flags. Checked = active/needed. Cleared once handled. -->
- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues
<!-- Keep only active issues here. Move resolved items to HISTORY.md. -->
- [ ] Arch.0.1: Service policy decisions pending
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human review confirms constraints for authentication posture, retention window, and max workload profile.
  - Notes: Decisions tracked in `.architecture/PLAN.md` as Arch-0.1 to Arch-0.3.
