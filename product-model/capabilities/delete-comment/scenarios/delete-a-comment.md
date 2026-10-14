---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Delete on an Item removed entry and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product deletes the comment permanently
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: removes
    from: Discarded
  contexts:
    web:
      place: web::signed-in::thread
---

# Delete a comment permanently

## Trigger

A thread admin, or an author allowed to, wants a discarded comment gone for good.

## Outcome

The comment is gone and cannot be restored.
