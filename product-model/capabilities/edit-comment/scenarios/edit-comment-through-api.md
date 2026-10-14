---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends new text for a comment
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product saves the comment and records the edit
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: changes
    facts:
    - Body
    - Edited at
  contexts:
    web:
      place: api
---

# Edit a comment through the API

## Trigger

An integration acting as a person changes their comment.

## Outcome

The comment shows the new text and is marked Edited.
