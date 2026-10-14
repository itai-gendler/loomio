---
kind: primary
routes:
  web: Web
steps:
- text: The closing time has passed
  kind: condition
  unattended: true
  entities:
  - entity: poll
    effect: reads
    facts:
    - Closing time
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product closes voting, counts an STV Election, publishes vote reasons hidden until closing and notifies the poll's author
  kind: product
  entities:
  - entity: poll
    effect: changes
    from: Open
    to: Closed
    facts:
    - Closed at
    - Results
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# A poll closes at its closing time

## Trigger

A poll's closing time passes.

## Outcome

Voting is closed and the poll's author is notified.
