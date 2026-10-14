---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Move item, ticks further items and chooses the destination thread
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product moves the selected items into the destination thread
  kind: product
  actor: user
  entities:
  - entity: comment
    effect: changes
    facts:
    - Thread
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Move comments to another thread

## Trigger

A conversation inside a thread belongs elsewhere.

## Outcome

The selected items are in the destination thread.

## Edge cases

- A standalone poll can be moved into a discussion the same way.
- Moving into a new discussion starts it with the title and context given.
