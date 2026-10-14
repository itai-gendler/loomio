---
kind: edge
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
- text: The organization has reached its plan's thread limit
  kind: condition
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Thread limit
  - entity: thread
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

# Starting a discussion beyond the plan's thread limit is refused

## Trigger

The organization already holds as many threads as its plan allows.

## Outcome

No discussion is created.
