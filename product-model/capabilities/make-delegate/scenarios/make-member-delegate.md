---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Make delegate for a member
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the member a delegate and notifies them
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    facts:
    - Delegate
  contexts:
    web:
      place: web::signed-in::group
---

# Make a member a delegate

## Trigger

An admin records who holds voting rights in the group.

## Outcome

The member is a delegate and has been notified.
