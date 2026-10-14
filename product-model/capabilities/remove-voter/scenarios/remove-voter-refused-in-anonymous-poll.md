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
- text: The User looks for a way to remove a voter
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product offers no way to remove anyone
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Removing a voter from an anonymous poll is refused

## Trigger

A poll admin looks to remove someone from an anonymous poll.

## Outcome

Nobody is removed.
