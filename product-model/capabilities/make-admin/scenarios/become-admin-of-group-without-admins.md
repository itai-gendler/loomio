---
kind: alternative
routes:
  web: Web
steps:
- text: The group has no admins
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Admin count
  contexts:
    web:
      place: web::signed-in::group
- text: The User selects Become admin
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the User an admin
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

# A member becomes admin of a group with no admins

## Trigger

A group has been left without any admin.

## Outcome

The member who stepped forward is the group's admin.
