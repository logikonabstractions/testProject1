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
Define a cloud-native, micro-service architecture for browser-based document conversion across common text and geospatial formats.

## Active assumptions / constraints
<!-- Keep only the assumptions or constraints that materially affect the current architecture draft. -->
- Cloud-native deployment model.
- Micro-service decomposition is required.
- In-scope conversions are text and geospatial document formats; media formats are excluded.
- MVP-first evolution with progressive expansion of supported format pairs.

## Work log (current session)
<!-- Append-only bullets for what changed and why. Prefer file/section references. -->
- 2026-03-06: Created initial architecture draft in `.architecture/ARCHITECTURE_DESCRIPTION.md` with component responsibilities, interfaces, interactions, and system-wide concerns.
- 2026-03-06: Updated active architecture tracking to `IN_REVIEW` pending human feedback on open questions.

## Workflow state
<!-- Dispatcher flags. Checked = active/needed. Cleared once handled. -->
- [x] PROBLEM_CLARIFIED
- [x] DRAFT_CREATED
- [x] HUMAN_REVIEW_REQUIRED
- [ ] DECISIONS_CAPTURED

## Active issues
<!-- Keep only active issues here. Move resolved items to HISTORY.md. -->
- [ ] Arch.0.1: MVP access and job completion interaction model
  - Impact: QUESTION <!-- QUESTION | MINOR | MAJOR | BLOCKER -->
  - Status: IN_REVIEW <!-- one of: NOT_STARTED | IN_PROGRESS | IN_REVIEW | DONE -->
  - Unblock condition: Human reviewer confirms authentication posture and completion notification approach for MVP.
  - Notes: Impacts API edge behavior, delivery coordinator requirements, and user flow complexity.
