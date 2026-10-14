---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the group's notification settings and chooses how to stay updated
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product saves the setting for the group and its threads
  kind: product
  actor: user
  entities:
  - entity: membership
    effect: changes
    facts:
    - Email notifications
  - entity: thread-member
    effect: changes
    facts:
    - Email notifications
  - entity: thread
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Change notifications for a group

## Trigger

A member wants to follow a busy group less closely.

## Outcome

The group and its threads use the chosen setting for the member.

## Edge cases

- Admins cannot change other people's notification settings.
