---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Leave group and confirms
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product removes the User from the group and its subgroups and removes their votes from the group's open polls
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    from: Active
    to: Removed
    facts: []
  - entity: thread-member
    effect: changes
    facts:
    - Guest
  - entity: vote
    effect: changes
    from: Cast
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

# Leave a group

## Trigger

A member no longer wants to take part.

## Outcome

The person is no longer a member of the group or its subgroups, and their votes no longer count in its open polls.

## Edge cases

- Leaving while a poll is closed gives no vote back if it is later reopened.
