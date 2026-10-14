---
kind: primary
routes:
  web: Web
steps:
- text: No poll in the thread is active
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User selects Lock thread
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product locks the thread
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Locked
  contexts:
    web:
      place: web::signed-in::thread
---

# Lock a thread

## Trigger

A thread admin considers the conversation finished.

## Outcome

The thread is locked and marked Locked, and leaves the list of open discussions.

## Edge cases

- While locked, nobody comments, starts, edits, deletes or reopens polls, or edits comments in the thread.
