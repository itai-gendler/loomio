---
kind: primary
routes:
  web: Web
steps:
- text: The User selects the reaction button on an item and picks an emoji
  kind: actor
  actor: user
  entities:
  - entity: reaction
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The thread allows reactions
  kind: condition
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts:
    - Allow reactions
  - entity: reaction
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product adds the reaction and notifies the item's author in Loomio
  kind: product
  actor: user
  entities:
  - entity: reaction
    effect: creates
    facts:
    - Emoji
  contexts:
    web:
      place: web::signed-in::thread
---

# React to an item

## Trigger

Someone wants to acknowledge a comment without writing one.

## Outcome

The reaction shows under the item and its author is notified in Loomio.
