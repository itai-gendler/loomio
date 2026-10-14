---
kind: validation
routes:
  web: Web
steps:
- text: The User replies to a notification email
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: email
- text: The comment is not allowed or is invalid
  kind: condition
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts:
    - Locked
    - Allow comments
  - entity: comment
    effect: reads
    facts: []
  contexts:
    web:
      place: email
- text: The Product emails the User that the reply was not posted
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: email
---

# An email reply that cannot be posted is returned

## Trigger

A reply by email cannot become a comment, for example because the thread is locked.

## Outcome

No comment is added and the sender is emailed why, at most once an hour.
