---
kind: alternative
routes:
  web: Web
steps:
- text: The group lets admins edit member comments
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Admins can edit member comments
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User edits another member's comment
  kind: actor
  actor: user
  entities:
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

# An admin edits a member's comment

## Trigger

The group has agreed admins may moderate member content.

## Outcome

The comment shows the admin's change, recorded with who made it.
