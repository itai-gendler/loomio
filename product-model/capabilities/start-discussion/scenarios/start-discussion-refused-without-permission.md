---
kind: validation
routes:
  web: Web
steps:
- text: The User submits a new discussion
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: Members of the group may not start discussions and the User is not an admin
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Members can start discussions
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product refuses to start the discussion
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-form
---

# Starting a discussion is refused without permission

## Trigger

A member tries to start a discussion in a group where members may not.

## Outcome

No discussion is created.
