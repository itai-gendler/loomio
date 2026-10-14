---
kind: alternative
routes:
  web: Web
steps:
- text: The User picks group members or the whole group and writes an optional message
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product notifies the chosen members
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Notify group members about a thread

## Trigger

Someone wants members who already have access to look at the thread.

## Outcome

The chosen members are notified and nobody's access changes.
