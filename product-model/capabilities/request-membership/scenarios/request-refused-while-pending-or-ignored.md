---
kind: validation
routes:
  web: Web
steps:
- text: The User answers the joining prompt
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The User's last request is still pending or was ignored
  kind: condition
  actor: user
  entities:
  - entity: membership-request
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product refuses the request as already made
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
---

# A repeated request is refused

## Trigger

A person asks again while their request is still pending, or after it was ignored.

## Outcome

No new request is recorded.

## Edge cases

- A member of the group cannot request to join it.
