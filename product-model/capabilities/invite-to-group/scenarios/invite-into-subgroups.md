---
kind: alternative
routes:
  web: Web
steps:
- text: The User enters people and ticks the subgroups they should join
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The organization's plan is active and has room for the new members
  kind: condition
  actor: user
  entities:
  - entity: subscription
    effect: reads
    facts:
    - Status
    - Member limit
  contexts:
    web:
      place: web::signed-in::group
- text: The Product invites newcomers to each chosen group and adds people who already belong to the organization as accepted members
  kind: product
  actor: user
  entities:
  - entity: membership
    as: invitation
    effect: creates
    to: Invited
    facts:
    - Role
    - Delegate
    - Vote weight
    - Invited by
  - entity: membership
    as: existing-member
    effect: creates
    to: Active
    facts:
    - Role
    - Delegate
    - Vote weight
    - Accepted at
    - Invited by
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Invite people into subgroups at once

## Trigger

An admin wants new people to land in the right teams straight away.

## Outcome

Each invitee holds a Membership in every chosen group; people already in the organization are members of the new subgroups without accepting.
