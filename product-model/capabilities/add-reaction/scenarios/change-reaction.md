---
kind: alternative
routes:
  web: Web
steps:
- text: The User picks another emoji
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product changes the reaction
  kind: product
  actor: user
  entities:
  - entity: reaction
    effect: changes
    facts:
    - Emoji
  contexts:
    web:
      place: web::signed-in::thread
---

# Change a reaction

## Trigger

Someone picks a different emoji for an item they already reacted to.

## Outcome

The item shows the new emoji.
