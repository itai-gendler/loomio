---
kind: validation
routes:
  web: Web
steps:
- text: The User's integration sends a member list
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: api
- text: The User is not an admin of the group
  kind: condition
  actor: user
  entities:
  - entity: membership
    effect: reads
    facts:
    - Role
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product refuses the request
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: api
---

# Syncing members is refused for non-admins

## Trigger

Someone who is not an admin of the group tries to sync its members.

## Outcome

Nothing changes.
