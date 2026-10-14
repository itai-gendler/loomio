---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Join group and answers the joining prompt
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The group requires approval to join
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - How people join
    - Joining prompt
  contexts:
    web:
      place: web::signed-in::group
- text: The Product records the request and notifies the group's admins
  kind: product
  actor: user
  entities:
  - entity: membership-request
    effect: creates
    to: Pending
    facts:
    - Introduction
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Request to join a group

## Trigger

A person who can see a group that requires approval wants to join.

## Outcome

A pending request with the person's introduction waits for review and the admins are notified.
