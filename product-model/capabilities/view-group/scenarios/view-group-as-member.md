---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the group
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product shows the group with its threads, polls and members
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
    - Description
    - Privacy
  - entity: thread
    effect: reads
    facts:
    - Pinned
    - Locked
    - Last activity
  - entity: discussion
    effect: reads
    facts:
    - Title
  - entity: poll
    effect: reads
    facts:
    - Title
    - Closing time
  - entity: membership
    effect: reads
    facts:
    - Role
    - Delegate
    - Title
  contexts:
    web:
      place: web::signed-in::group
---

# View a group as a member

## Trigger

A member opens their group.

## Outcome

The member sees the group's threads, private ones included, its polls and its members.

## Edge cases

- Locked threads are left out of the list unless the viewer asks for all threads.
