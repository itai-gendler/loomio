---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Pin thread
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product pins the thread
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Pinned
  contexts:
    web:
      place: web::signed-in::thread
---

# Pin a thread

## Trigger

A thread admin wants a welcome discussion or announcement at the top.

## Outcome

The thread appears above the group's other threads.
