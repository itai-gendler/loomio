---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Join group
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The group lets people join without approval
  kind: condition
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - How people join
  contexts:
    web:
      place: web::signed-in::group
- text: The Product makes the User an active member and drops any membership request they had pending
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: creates
    to: Active
    facts:
    - Role
    - Delegate
    - Vote weight
    - Accepted at
  - entity: membership-request
    effect: removes
    from: Pending
  contexts:
    web:
      place: web::signed-in::group
---

# Join a group that needs no approval

## Trigger

A person who can see the group wants to take part.

## Outcome

The person is an active member, and any request they had pending is gone.

## Edge cases

- A person whose account email is not verified, or whose account is deactivated, cannot join.
