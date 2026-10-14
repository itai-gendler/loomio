---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Timeline or Threaded, newest or oldest first, and whether comments, reactions and concurrent polls are allowed
  kind: actor
  actor: user
  entities:
  - entity: reaction
    effect: reads
    facts: []
  - entity: comment
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product saves the settings and rearranges the thread when the arrangement changed
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Reply arrangement
    - Allow comments
    - Allow reactions
    - Concurrent polls
    - Comment length limit
  contexts:
    web:
      place: web::signed-in::thread
---

# Change thread settings

## Trigger

A thread admin wants replies grouped beneath what they answer and two polls at once.

## Outcome

Everyone sees the thread arranged as chosen and the thread accepts what the settings allow.
