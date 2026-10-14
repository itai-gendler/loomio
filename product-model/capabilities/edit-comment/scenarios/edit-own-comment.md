---
kind: primary
routes:
  web: Web
steps:
- text: The User edits their comment
  kind: actor
  actor: user
  entities:
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The group lets members edit their comments
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Members can edit comments
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
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
      place: web::signed-in::thread
---

# Edit your own comment

## Trigger

An author wants to correct their comment.

## Outcome

The comment shows the new text and is marked Edited.
