---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to edit the poll
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: Voting has closed
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Closed at
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product offers no way to edit it
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Editing a closed poll is refused

## Trigger

Someone tries to edit a poll whose voting has closed.

## Outcome

Nothing changes; the poll must be reopened first.
