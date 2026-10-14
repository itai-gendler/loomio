---
kind: alternative
routes:
  web: Web
steps:
- text: The Instance administrator confirms removing a member
  kind: actor
  actor: instance-administrator
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product removes the person from the group and its subgroups and removes their votes from the group's open polls
  kind: product
  actor: instance-administrator
  entities:
  - entity: membership
    effect: changes
    from: Active
    to: Removed
    facts: []
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

# An instance administrator removes a member

## Trigger

An instance administrator removes someone from a group they do not administer.

## Outcome

The person has no access to the group and their votes no longer count in open polls.
