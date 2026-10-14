---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor opens the thread
  kind: actor
  actor: visitor
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::thread
- text: The thread is private
  kind: condition
  actor: visitor
  entities:
  - entity: thread
    effect: reads
    facts:
    - Private
  contexts:
    web:
      place: web::public::thread
- text: The Product shows nothing of the thread and offers to sign in
  kind: product
  actor: visitor
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::thread
---

# A private thread is refused to outsiders

## Trigger

Someone who is neither a member of the group nor a guest opens a private thread.

## Outcome

Nothing in the thread is shown.
