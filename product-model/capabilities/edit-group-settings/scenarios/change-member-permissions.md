---
kind: primary
routes:
  web: Web
steps:
- text: The User turns member permissions on or off
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group-settings
- text: The Product saves the group's permissions
  kind: product
  actor: user
  entities:
  - entity: group
    effect: changes
    facts:
    - Members can add members
    - Members can add guests
    - Members can announce
    - Members can start discussions
    - Non-members can start discussions
    - Members can edit discussions
    - Members can edit comments
    - Members can delete comments
    - Members can start polls
    - Members can create subgroups
    - Members can create tags
    - Members can create templates
    - Admins can edit member comments
  contexts:
    web:
      place: web::signed-in::group-settings
---

# Change what members may do

## Trigger

An admin wants ordinary members to start polls but no longer add members.

## Outcome

Members may take exactly the actions the permissions now allow; admins keep every ability.

## Edge cases

- Changing the handle keeps the previous addresses redirecting to the group.
