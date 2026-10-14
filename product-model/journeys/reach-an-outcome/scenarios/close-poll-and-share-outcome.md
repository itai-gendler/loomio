---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User selects Close early and confirms
  kind: actor
  capability: close-poll
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product closes voting
  kind: product
  capability: close-poll
  actor: user
  entities:
  - entity: poll
    effect: changes
    from: Open
    to: Closed
    facts:
    - Closed at
    - Results
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product opens the form to share an outcome
  kind: product
  capability: close-poll
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
- text: The User writes the outcome and picks people to notify
  kind: actor
  capability: share-outcome
  actor: user
  entities:
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product publishes the outcome above the results and notifies the chosen people
  kind: product
  capability: share-outcome
  actor: user
  entities:
  - entity: outcome
    effect: creates
    to: Current
    facts:
    - Statement
    - Review date
    - Chosen option
    - Event location
  contexts:
    web:
      place: web::signed-in::thread
---

# Close a poll and share its outcome

## Trigger

A poll admin decides voting has run its course.

## Outcome

Voting is closed and the outcome is shared with the people chosen.
