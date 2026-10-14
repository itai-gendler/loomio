---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Make admin for a member
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the member an admin and notifies them
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

# An admin makes a member an admin

## Trigger

An admin wants another trusted person able to administer the group.

## Outcome

The member is an admin and has been notified.

## Edge cases

- People can be made admins before they accept their invitation.
