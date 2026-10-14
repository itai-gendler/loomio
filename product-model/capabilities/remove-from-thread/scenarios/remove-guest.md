---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Remove from discussion for a guest
  kind: actor
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product removes the guest's access to the thread
  kind: product
  actor: user
  entities:
  - entity: thread-member
    effect: changes
    from: Active
    to: Removed
    facts: []
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Remove a guest from a thread

## Trigger

A thread admin decides a guest should no longer take part.

## Outcome

The guest can no longer open the thread.
