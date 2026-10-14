---
kind: primary
routes:
  web: Web
steps:
- text: The User confirms deleting the poll
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product deletes the poll and takes its votes out of the thread
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: changes
    from: Open
    to: Deleted
    facts: []
  - entity: thread
    effect: reads
    facts: []
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Delete a poll

## Trigger

A poll admin decides a poll should not stand.

## Outcome

The poll is deleted and its votes no longer show in the thread.
