---
kind: validation
routes:
  web: Web
steps:
- text: The User saves the poll
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The change touches anonymity, results hidden until closing, or an anonymous poll's ballot settings after a ballot
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Anonymous
    - Hide results
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product refuses the change
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
---

# Changing fixed settings is refused

## Trigger

A poll admin tries to change anonymity, show results hidden until closing, or change an anonymous poll's ballot settings after someone voted.

## Outcome

Nothing is saved.
