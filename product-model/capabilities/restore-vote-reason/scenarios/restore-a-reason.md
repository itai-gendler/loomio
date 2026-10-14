---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Restore on a redacted vote
  kind: actor
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product shows the reason again
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: changes
    facts:
    - Reason redacted
  contexts:
    web:
      place: web::signed-in::thread
---

# Restore a redacted reason

## Trigger

A poll admin decides a redacted reason can be shown.

## Outcome

The reason shows again.
