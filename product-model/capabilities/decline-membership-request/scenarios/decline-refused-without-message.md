---
kind: validation
routes:
  web: Web
steps:
- text: The User declines a request without a message
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product refuses to decline it without a message
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
---

# Declining without a message is refused

## Trigger

A reviewer tries to decline without writing a message.

## Outcome

The request stays pending.

## Edge cases

- The message is limited to 500 characters.
