---
kind: alternative
routes:
  web: Web
steps:
- text: The User follows the group's shared link
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the User an active member
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

# Join through the group's shared link

## Trigger

Someone follows a group's shared link from an email, newsletter or website.

## Outcome

The person is an active member of the group.

## Edge cases

- Resetting the link stops the old one from working.
