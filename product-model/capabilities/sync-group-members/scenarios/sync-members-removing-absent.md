---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends the addresses and asks to remove absent members
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: api
- text: The Product invites the new addresses, removes members whose address is not listed and reports both
  kind: product
  actor: user
  entities:
  - entity: membership
    as: added
    effect: creates
    to: Invited
    facts:
    - Role
    - Delegate
    - Vote weight
    - Invited by
  - entity: membership
    as: removed
    effect: changes
    from: Active
    to: Removed
    facts: []
  contexts:
    web:
      place: api
---

# Sync members and remove those not listed

## Trigger

The integration asks for members missing from the list to be removed.

## Outcome

The group's members match the list.
