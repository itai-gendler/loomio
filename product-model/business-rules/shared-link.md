---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts:
  - Shared link
permits:
- related:
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - fact: Members can add members
    is: true
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/groups_controller.rb#reset_token
---

# Admins reset a group's shared link, and members do when the group lets them add members

Anyone holding the link can join the group; resetting it stops the old one working.
