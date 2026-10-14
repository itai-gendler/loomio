---
kind: alternative
routes:
  web: Web
steps:
- text: The poll already has an outcome
  kind: condition
  actor: user
  entities:
  - entity: outcome
    as: earlier
    effect: reads
    facts:
    - Statement
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User writes a fresh statement of what was decided
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product makes the new outcome current and keeps the earlier one
  kind: product
  actor: user
  entities:
  - entity: outcome
    as: earlier
    effect: changes
    from: Current
    to: Superseded
    facts: []
  - entity: outcome
    as: new
    effect: creates
    to: Current
    facts:
    - Statement
    - Review date
    - Chosen option
    - Event location
  contexts:
    web:
      place: web::signed-in::thread
---

# Share a new outcome

## Trigger

A poll already has an outcome and someone shares a new one.

## Outcome

The new outcome is current and the earlier one is kept.
