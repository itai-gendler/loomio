---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Unlock thread
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product unlocks the thread
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Locked
  contexts:
    web:
      place: web::signed-in::thread
---

# Unlock a thread

## Trigger

A thread admin wants to resume a locked conversation.

## Outcome

The thread accepts comments and changes again.
