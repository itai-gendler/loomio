---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Demote admin for a thread admin
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product removes the person's thread admin role
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

# Demote a thread admin

## Trigger

A thread admin decides someone no longer needs to manage the thread.

## Outcome

The person no longer administers the thread.
