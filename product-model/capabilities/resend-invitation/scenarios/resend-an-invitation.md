---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Resend invitation for someone who has not accepted
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product sends the invitation again
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: reads
    facts:
    - Accepted at
  contexts:
    web:
      place: web::signed-in::group
---

# Resend an invitation

## Trigger

An invitee lost or forgot their invitation email.

## Outcome

The invitee receives the invitation again.
