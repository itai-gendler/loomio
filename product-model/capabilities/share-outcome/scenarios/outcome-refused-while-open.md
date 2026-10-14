---
kind: validation
routes:
  web: Web
steps:
- text: Voting is still open
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
- text: The User looks for a way to share an outcome
  kind: actor
  actor: user
  entities:
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product offers no way to share an outcome yet
  kind: product
  actor: user
  entities:
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# An outcome is refused while voting is open

## Trigger

Someone looks to share an outcome before voting ends.

## Outcome

No outcome is shared.
