---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Cancel invitation for someone who has not accepted
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product cancels the invitation and removes the person's undecided votes in the group's open polls
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    from: Invited
    to: Removed
    facts: []
  - entity: vote
    effect: changes
    from: Undecided
    to: Removed
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

# Cancel a pending invitation

## Trigger

An admin, or the person who sent it, decides an invitation was a mistake.

## Outcome

The invitation no longer works and the invitee holds no undecided votes in the group's open polls.
