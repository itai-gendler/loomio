---
kind: edge
routes:
  web: Web
steps:
- text: The User posts a reply
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The item being replied to was deleted or discarded
  kind: condition
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product refuses the reply
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Replying to a removed item is refused

## Trigger

Someone replies to an item that was deleted or discarded meanwhile.

## Outcome

No reply is added.
