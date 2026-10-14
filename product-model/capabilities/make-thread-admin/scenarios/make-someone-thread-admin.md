---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Make admin for a person in the thread
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product makes the person an admin of the thread
  kind: product
  actor: user
  entities:
  - entity: thread-member
    effect: changes
    facts:
    - Thread admin
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Make someone a thread admin

## Trigger

A thread admin wants help running the thread.

## Outcome

The person administers the thread.
