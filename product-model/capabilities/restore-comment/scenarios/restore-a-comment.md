---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Restore on an Item removed entry
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product restores the comment
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: changes
    from: Discarded
    to: Visible
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Restore a discarded comment

## Trigger

The author who discarded a comment, or a thread admin, wants it back.

## Outcome

The comment shows in the thread again.
