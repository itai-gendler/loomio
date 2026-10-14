---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration asks to delete a poll
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product deletes the poll
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: changes
    from: Open
    to: Deleted
    facts: []
  contexts:
    web:
      place: api
---

# Delete a poll through the API

## Trigger

An integration acting as a poll admin deletes a poll.

## Outcome

The poll is deleted.
