---
kind: primary
routes:
  web: Web
steps:
- text: The User ignores a pending request
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product closes the request without notifying the requester
  kind: product
  actor: user
  entities:
  - entity: membership-request
    effect: changes
    from: Pending
    to: Ignored
    facts:
    - Responded by
  contexts:
    web:
      place: web::signed-in::group
---

# Ignore a request to join

## Trigger

A reviewer decides a request needs no answer.

## Outcome

The request is closed, the requester is not told, and they cannot request again.
