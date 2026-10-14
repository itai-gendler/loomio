---
kind: alternative
routes:
  web: Web
steps:
- text: The User follows the invitation link
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product accepts the invitation, with every other pending invitation in the same organization, and notifies the inviter
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    from: Invited
    to: Active
    facts:
    - Accepted at
  contexts:
    web:
      place: web::signed-in::group
---

# Accept an invitation while signed in

## Trigger

A signed-in person opens an invitation link.

## Outcome

The person is an active member of the group.
