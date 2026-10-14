---
kind: validation
routes:
  web: Web
steps:
- text: The poll is anonymous
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Anonymous
  contexts:
    web:
      place: web::signed-in::thread
- text: The User looks for a way to reopen the poll
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product offers no way to reopen it
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Reopening an anonymous poll is refused

## Trigger

A poll admin looks to reopen a closed anonymous poll.

## Outcome

The poll stays closed.
