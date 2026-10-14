---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends new details, options or closing time
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: api
- text: The Product saves the poll
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: changes
    facts:
    - Details
    - Options
    - Closing time
  contexts:
    web:
      place: api
---

# Edit a poll through the API

## Trigger

An integration acting as a poll admin changes a poll that has not closed.

## Outcome

The poll shows the changes.
