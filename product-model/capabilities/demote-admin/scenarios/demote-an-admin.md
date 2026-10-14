---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Demote admin for an admin
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the admin an ordinary member
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

# Demote an admin to member

## Trigger

An admin decides someone no longer needs to administer the group.

## Outcome

The person is an ordinary member.

## Edge cases

- An admin may also step down from the role themselves.
