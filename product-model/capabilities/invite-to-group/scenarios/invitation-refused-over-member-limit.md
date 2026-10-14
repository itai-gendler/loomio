---
kind: edge
routes:
  web: Web
steps:
- text: The User sends invitations
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The plan has lapsed or the new members would exceed its member limit
  kind: condition
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Status
    - Member limit
  contexts:
    web:
      place: web::signed-in::group
- text: The Product refuses the invitations
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
---

# Invitations beyond the plan are refused

## Trigger

The organization's plan has lapsed, or the invitations would take it past its member limit.

## Outcome

Nobody is invited.
