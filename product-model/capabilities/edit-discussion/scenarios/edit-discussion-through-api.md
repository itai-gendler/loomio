---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a new title or context
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: api
- text: The Product saves the discussion
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: changes
    facts:
    - Title
    - Context
  contexts:
    web:
      place: api
---

# Edit a discussion through the API

## Trigger

An integration acting as a person changes a discussion.

## Outcome

The discussion shows the new title and context.
