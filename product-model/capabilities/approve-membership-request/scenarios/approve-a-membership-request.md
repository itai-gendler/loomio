---
kind: primary
routes:
  web: Web
steps:
- text: The User approves a pending request
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product marks the request approved, makes the requester an active member and notifies them
  kind: product
  actor: user
  entities:
  - entity: membership-request
    effect: changes
    from: Pending
    to: Approved
    facts:
    - Responded by
  - entity: membership
    effect: creates
    to: Active
    facts:
    - Role
    - Delegate
    - Vote weight
    - Accepted at
  contexts:
    web:
      place: web::signed-in::group
---

# Approve a request to join

## Trigger

A reviewer reads a pending request and wants the person in the group.

## Outcome

The requester is an active member and has been notified.

## Edge cases

- A request already answered cannot be answered again.
