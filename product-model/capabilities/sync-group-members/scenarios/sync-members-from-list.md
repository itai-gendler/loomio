---
kind: primary
routes:
  web: Web
steps:
- text: The User's integration sends the group's email addresses
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product invites the addresses that are not yet members and reports who was added
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: creates
    to: Invited
    facts:
    - Role
    - Delegate
    - Vote weight
    - Invited by
  contexts:
    web:
      place: api
---

# Sync members from a list

## Trigger

A group admin's integration sends the current member list from another system.

## Outcome

Everyone on the list is invited or already a member.
