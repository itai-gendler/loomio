---
kind: alternative
routes:
  web: Web
steps:
- text: The User invites a person who used to be a member
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The person's earlier Membership was removed
  kind: condition
  actor: user
  entities:
  - entity: membership
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product turns the earlier Membership back into an invitation, as an ordinary member, and gives back their votes in the group's polls that are still open
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    from: Removed
    to: Invited
    facts:
    - Role
    - Invited by
    - Accepted at
  - entity: vote
    effect: changes
    from: Removed
    to: Undecided
    facts: []
  - entity: group
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Invite a former member again

## Trigger

An admin invites someone who left or was removed earlier.

## Outcome

The person holds a fresh invitation as an ordinary member, and their earlier votes in polls still open are back.
