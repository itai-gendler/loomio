---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses to give everyone one weight and enters it
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::member-weights
- text: The Product gives every active member that weight
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

# Give every member the same weight

## Trigger

An admin resets everyone to one value.

## Outcome

Every active member has the chosen weight.
