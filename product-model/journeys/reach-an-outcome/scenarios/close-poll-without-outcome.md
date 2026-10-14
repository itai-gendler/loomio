---
kind: alternative
result: not-achieved
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
- text: The Product closes voting and opens the form to share an outcome
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
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User dismisses the form without sharing an outcome
  kind: actor
  actor: user
  entities:
  - entity: outcome
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Close a poll and leave the outcome for later

## Trigger

A poll admin closes a poll but is not ready to state the outcome.

## Outcome

Voting is closed and the poll has no outcome yet.
