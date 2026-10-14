---
kind: validation
routes:
  web: Web
steps:
- text: The User follows an invitation link
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The invitation was already accepted
  kind: condition
  actor: user
  entities:
  - entity: membership
    effect: reads
    facts:
    - Accepted at
  contexts:
    web:
      place: web::signed-in::group
- text: The Product reports the invitation as already used
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
---

# A used invitation link is refused

## Trigger

Someone opens an invitation link that was already accepted.

## Outcome

No Membership changes.

## Edge cases

- An invitation to a group under a lapsed plan accepts nothing.
