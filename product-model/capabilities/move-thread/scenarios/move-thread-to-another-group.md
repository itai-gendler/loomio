---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Move thread and chooses a group they may start discussions in
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  - entity: thread
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product moves the thread, sets its privacy from the new group, gives that group's members votes in its open polls and adds a moved item to the thread
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Group
    - Private
  - entity: group
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Move a thread to another group

## Trigger

A thread admin finds a discussion belongs in another group.

## Outcome

The thread is in the new group with that group's privacy, and the new group's members can vote in its open polls.
