---
kind: alternative
routes:
  web: Web
steps:
- text: The User is a member of the subgroup and an admin of its parent group
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Parent group
  contexts:
    web:
      place: web::signed-in::group
- text: The User selects Become admin on the subgroup
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the User an admin of the subgroup
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    facts:
    - Role
  contexts:
    web:
      place: web::signed-in::group
---

# A parent group admin becomes admin of a subgroup

## Trigger

An admin of an organization has joined one of its subgroups.

## Outcome

The parent group admin administers the subgroup too.
