---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration asks to delete a comment
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: api
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
      place: api
---

# Discard a comment through the API

## Trigger

An integration acting as a person removes a comment.

## Outcome

The comment's place shows Item removed.
