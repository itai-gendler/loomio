---
kind: validation
routes:
  web: Web
steps:
- text: The User submits a new poll
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: Another poll in the thread is active and the thread does not allow concurrent polls
  kind: condition
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts:
    - Concurrent polls
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product refuses to start the poll
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
---

# A second active poll is refused

## Trigger

Someone starts a poll in a thread that already has an active poll.

## Outcome

No poll is created.

## Edge cases

- An STV Election needs more candidates than seats.
