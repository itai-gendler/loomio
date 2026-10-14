---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the thread's notification control and chooses a setting
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product saves the setting for this thread
  kind: product
  actor: user
  entities:
  - entity: thread-member
    effect: changes
    facts:
    - Email notifications
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Change notifications for a thread

## Trigger

A person wants every update from an important thread.

## Outcome

The thread uses the chosen setting for the person; the group keeps its own.
