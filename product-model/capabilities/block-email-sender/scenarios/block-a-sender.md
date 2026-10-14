---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Reject for the email
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product blocks the address for the group and rejects the email
  kind: product
  actor: user
  entities:
  - entity: email-alias
    effect: creates
    facts:
    - Address
    - Added by
  - entity: unrecognized-email
    effect: changes
    from: Waiting
    to: Rejected
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Block a sender

## Trigger

An admin sees an email from an address that should not post.

## Outcome

The email is rejected and later email from the address is dropped.
