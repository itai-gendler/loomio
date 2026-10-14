---
kind: validation
routes:
  web: Web
steps:
- text: The User submits a new top-level group
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::start-group
- text: Group creation is disabled on the server
  kind: condition
  actor: user
  entities:
  - entity: server-settings
    effect: reads
    facts:
    - Group creation
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::start-group
- text: The Product refuses to create the group
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::start-group
---

# Starting a group is refused while group creation is disabled

## Trigger

A person who is not an instance administrator tries to start a top-level group on a server that has turned group creation off.

## Outcome

No group is created.
