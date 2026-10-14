---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Deactivate account and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
- text: The Product deactivates the account, removes it from every group, removes its undecided votes, drops its pending membership requests and stops all email
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Deactivated
  - entity: membership
    effect: changes
    from: Active
    to: Removed
    facts: []
  - entity: vote
    effect: changes
    from: Undecided
    to: Removed
    facts: []
  - entity: membership-request
    effect: removes
    from: Pending
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::profile
---

# Deactivate your account

## Trigger

A person wants to stop taking part without erasing their contributions.

## Outcome

The account is deactivated, belongs to no group and receives no email; votes it cast still count.

## Edge cases

- A deactivated account can be reactivated later by contacting the server's operators.
