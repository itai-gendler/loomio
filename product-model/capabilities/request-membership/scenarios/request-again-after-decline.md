---
kind: alternative
routes:
  web: Web
steps:
- text: The User answers the joining prompt again
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The User's last request was declined with a message
  kind: condition
  actor: user
  entities:
  - entity: membership-request
    as: earlier
    effect: reads
    facts:
    - Decline reason
  contexts:
    web:
      place: web::signed-in::group
- text: The Product records the new request and notifies the group's admins
  kind: product
  actor: user
  entities:
  - entity: membership-request
    as: new
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

# Request again after a decline

## Trigger

A person whose earlier request was declined with a message asks again.

## Outcome

A new pending request waits for review.
