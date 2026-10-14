---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration asks to delete a discussion
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product deletes the discussion's thread with every poll in it
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  - entity: thread
    effect: changes
    from: Active
    to: Deleted
    facts: []
  - entity: poll
    as: open-poll
    effect: changes
    from: Open
    to: Deleted
    facts: []
  - entity: poll
    as: closed-poll
    effect: changes
    from: Closed
    to: Deleted
    facts: []
  contexts:
    web:
      place: api
---

# Delete a discussion through the API

## Trigger

An integration acting as a person deletes a discussion.

## Outcome

The discussion, its thread and its polls are deleted.
