---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Discard on a comment
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product discards the comment
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: changes
    from: Visible
    to: Discarded
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Discard a comment

## Trigger

An author regrets a comment, or a thread admin moderates one.

## Outcome

The comment's place shows Item removed.
