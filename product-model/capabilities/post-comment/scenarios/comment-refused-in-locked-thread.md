---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to comment
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The thread is locked or does not allow comments
  kind: condition
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts:
    - Locked
    - Allow comments
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product offers no way to comment
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Commenting in a locked thread is refused

## Trigger

Someone tries to comment in a thread that is locked or does not allow comments.

## Outcome

No comment is added.
