---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects Join group on a subgroup of a group they administer
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The subgroup is not secret
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Privacy
    - Parent group
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the User an active member of the subgroup
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: creates
    to: Active
    facts:
    - Role
    - Delegate
    - Vote weight
    - Accepted at
  contexts:
    web:
      place: web::signed-in::group
---

# A parent group admin joins a subgroup

## Trigger

An admin of an organization wants to take part in one of its subgroups.

## Outcome

The admin is an active member of the subgroup.
