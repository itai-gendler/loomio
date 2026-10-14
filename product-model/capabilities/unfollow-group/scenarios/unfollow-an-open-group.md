---
kind: primary
routes:
  web: Web
steps:
- text: The User turns off Follow updates
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product stops including the group in the User's catch-up
  kind: product
  actor: user
  entities:
  - entity: group-follow
    effect: removes
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Stop following a group

## Trigger

A follower no longer wants the group's updates.

## Outcome

The group is left out of the person's catch-up.
