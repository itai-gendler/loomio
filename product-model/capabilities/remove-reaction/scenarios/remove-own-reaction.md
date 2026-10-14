---
kind: primary
routes:
  web: Web
steps:
- text: The User selects their reaction to remove it
  kind: actor
  actor: user
  entities:
  - entity: reaction
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product removes the reaction
  kind: product
  actor: user
  entities:
  - entity: reaction
    effect: removes
  contexts:
    web:
      place: web::signed-in::thread
---

# Remove your reaction

## Trigger

Someone withdraws an emoji they added.

## Outcome

The reaction is gone.
