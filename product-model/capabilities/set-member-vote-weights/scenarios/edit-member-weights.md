---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a weight for each member and saves them
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::member-weights
- text: The Product saves the members' weights
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    facts:
    - Vote weight
  contexts:
    web:
      place: web::signed-in::member-weights
---

# Edit members' vote weights

## Trigger

A group's governance gives some members more or less say.

## Outcome

Members bring their weight into polls they are added to from now on; polls that already have them keep their weights.
