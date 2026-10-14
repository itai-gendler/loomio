---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a username
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
- text: Another account uses that username
  kind: condition
  actor: user
  entities:
  - entity: user
    effect: reads
    facts:
    - Username
  contexts:
    web:
      place: web::signed-in::profile
- text: The Product refuses the username
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
---

# A username already in use is refused

## Trigger

A person picks a username someone else has.

## Outcome

The profile is not saved.
