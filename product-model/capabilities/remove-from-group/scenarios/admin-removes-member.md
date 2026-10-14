---
kind: primary
routes:
  web: Web
steps:
- text: The User confirms removing a member
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product removes the person from the group and its subgroups, ends their guest access to the group's threads, and removes their votes from the group's open polls
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
    as: cast-vote
    effect: changes
    from: Cast
    to: Removed
    facts: []
  - entity: vote
    as: undecided-vote
    effect: changes
    from: Undecided
    to: Removed
    facts: []
  - entity: thread
    effect: reads
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

# An admin removes a member

## Trigger

An admin decides someone should no longer be part of the group.

## Outcome

The person has no access to the group, its subgroups or their private threads, and their votes no longer count in open polls.

## Edge cases

- A public poll stays readable to the former member, who cannot vote in it unless invited back.
- Inviting or adding the person back restores their access and their votes in polls still open.
