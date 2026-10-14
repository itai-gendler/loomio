---
kind: primary
routes:
  web: Web
steps:
- text: The group is Open and the User is not a member
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Privacy
  contexts:
    web:
      place: web::signed-in::group
- text: The User turns on Follow updates
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product starts including the group in the User's catch-up
  kind: product
  actor: user
  entities:
  - entity: group-follow
    effect: creates
    facts:
    - Followed since
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Follow an Open group

## Trigger

Someone wants to keep up with an Open group without joining.

## Outcome

The group's unread activity is included in the person's catch-up.

## Edge cases

- Following gives no membership, votes or immediate notifications.
- Joining the group ends following it.
