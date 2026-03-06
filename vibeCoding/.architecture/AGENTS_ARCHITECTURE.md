# ARCHITECTURE Workflow Contract

## Purpose

Translate a product or problem statement into an **architectural design**. This further specificies `AGENTS.md` for this mode.

## Instruction precedence & read order
1. As specified by `AGENTS.md`
2. This file
3. `.architecture/ARCHITECTURE_DESCRIPTION.md`
4. `.architecture/STATE.md`
5. `.architecture/PLAN.md`
6. `.architecture/HISTORY.md`

## Scope

This layer must define the major architectural parts of the target system, the responsibility of each, how they interact, and the main system-wide concerns.

It must not define implementation strategies or concrete technology choices (for example: specific frameworks, databases, cloud products, or vendors).

## Core output

The deliverable is a markdown document that gives a **structured architectural breakdown** of the proposed solution.

The output must:

- describe the target system in plain language
- identify the major architectural components required
- describe each component at the **functional type** level
- define responsibilities for each component
- capture the important interfaces and interactions between components
- capture relevant system-wide concerns, assumptions, constraints, and open questions
- conform to `.architecture/ARCHITECTURE_OUTPUT_FORMAT.md`

## Abstraction rule

Describe components by **role**, not by implementation choice.

Do **not** use concrete product names.

## Component rule

Architectural components must represent **one specific, meaningful system capabilities**. At the next abstraction layer, we should be able to select one specific technology to implement this capability.

Do not model low-level implementation artifacts as architectural components.

## Numbering rules

Use top-level component numbering in increments of 10:

- 10
- 20
- 30
- 40

## Architecture planning rule

Use `.architecture/PLAN.md` to track architecture questions that require discussion, investigation, clarification, or explicit decision. Do not over-use this track for minor decisions. Keep it for  blocking architectural choices.

Use `.architecture/STATE.md` to track the currently active architecture draft, current focus, active blockers, and work log.

Use `.architecture/HISTORY.md` to archive resolved questions, completed review rounds, and durable architecture decisions.