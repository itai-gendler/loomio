---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor opens the group's address
  kind: actor
  actor: visitor
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::group
- text: The group is Secret and the Visitor holds no invitation or link to it
  kind: condition
  actor: visitor
  entities:
  - entity: group
    effect: reads
    facts:
    - Privacy
  contexts:
    web:
      place: web::public::group
- text: The Product shows nothing about the group and offers to sign in
  kind: product
  actor: visitor
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::group
---

# A secret group stays hidden

## Trigger

Someone without access opens the address of a Secret group.

## Outcome

Nothing about the group is shown.
