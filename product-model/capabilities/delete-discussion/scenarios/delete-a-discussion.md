---
kind: primary
routes:
  web: Web
steps:
- text: The User confirms deleting the discussion
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
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
      place: web::signed-in::thread
---

# Delete a discussion

## Trigger

The author or a thread admin decides a discussion is not needed.

## Outcome

The discussion, its thread and its polls are deleted.

## Edge cases

- Locking keeps a thread available; deleting is meant for discussions that will not be needed again.
