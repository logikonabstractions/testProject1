# ARCHITECTURE DESCRIPTION

The response must provide one or more architectural component, adhering to this format and describes the solution.


# PROBLEM STATEMENT

## Objective

- System:
  - <what system is being designed>
- Users / actors:
  - <who it serves>
- Primary outcome:
  - <what it must enable>

## Scope boundaries

- In scope:
  - <items>
- Out of scope:
  - <items>

## Assumptions

- <assumptions>

## Architectural components

Repeat & fill this template as needed. Follow the numbering convention.

### 10 — <Component name>

- Category:
  - <client / domain service / orchestration / identity and access / data persistence / messaging / external integration / observability / other> 
- Purpose:
  - <why this exists>
- Responsibilities:
  - <responsibility>
- Interfaces:
  - Incoming:
    - <requests / commands / events / user actions / upstream inputs>
  - Outgoing:
    - <responses / commands / events / downstream outputs>
- Data / state:
  - <what data or state this component owns, reads, writes, persists, or exposes>
- Interactions:
  - User-facing:
    - <if applicable>
  - Internal synchronous:
    - <if applicable>
  - Internal asynchronous:
    - <if applicable>
- Security / access considerations:
  - <authentication / authorization / trust boundary / sensitive data notes>
- Observability / operational considerations:
  - <logging / monitoring / auditability / failure visibility / admin concerns>
- Dependencies:
  - <Components IDs>
- Constraints / notes:
  - <important remarks>
- Principal alternative (optional)
  - 1-2 sentence, do not systematically  include with all components. But when a there are strong reasons to consider 2 options as very close, describe here your 2nd best choice for this component.

## System interaction summary

- Primary request / control paths:
  - <summary>
- Primary data flows:
  - <summary>
- Primary event flows:
  - <summary>

## System-wide concerns

- Security and access control:
  - <items>
- Reliability and recovery:
  - <items>
- Observability and operations:
  - <items>
- Performance and scalability:
  - <items>
- Compliance / audit / governance:
  - <items if relevant>

## Open questions
- <question requiring architectural decision>
