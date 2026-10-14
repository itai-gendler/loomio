---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Reopen and sets a new closing time
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product opens voting again, clears an STV count and adds a reopened item to the thread without repeating opening notifications
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: changes
    from: Closed
    to: Open
    facts:
    - Closing time
    - Closed at
    - Results
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Reopen a poll

## Trigger

A poll admin wants more time for votes after closing.

## Outcome

Voting is open again until the new closing time; nobody is notified that it opened again.
