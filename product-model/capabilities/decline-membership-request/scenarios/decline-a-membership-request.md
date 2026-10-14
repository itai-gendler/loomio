---
kind: primary
routes:
  web: Web
steps:
- text: The User writes a message and declines the request
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product marks the request declined and sends the message to the requester
  kind: product
  actor: user
  entities:
  - entity: membership-request
    effect: changes
    from: Pending
    to: Declined
    facts:
    - Decline reason
    - Responded by
  contexts:
    web:
      place: web::signed-in::group
---

# Decline a request with a message

## Trigger

A reviewer decides not to admit the requester and explains why.

## Outcome

The request is declined and the requester has the message by email and notification.
