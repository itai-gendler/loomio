---
kind: validation
routes:
  web: Web
steps:
- text: The User adds people to the poll
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The poll is anonymous and not open
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
- text: The Product refuses to add anyone
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Adding voters to a closed anonymous poll is refused

## Trigger

Someone tries to add voters to an anonymous poll that is no longer open.

## Outcome

Nobody is added.
