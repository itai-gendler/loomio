---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Close early and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product closes voting, counts an STV Election and publishes vote reasons hidden until closing
  kind: product
  actor: user
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
- text: The Product opens the form to share an outcome
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Results
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Close a poll early

## Trigger

A poll admin decides enough people have voted.

## Outcome

Voting is closed, the results are final and the admin is asked to share an outcome.
