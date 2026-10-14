---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Unpin thread
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product unpins the thread
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

# Unpin a thread

## Trigger

A pinned thread no longer needs to stay at the top.

## Outcome

The thread takes its usual place.
