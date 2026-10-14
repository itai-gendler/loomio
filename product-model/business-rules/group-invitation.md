---
appliesTo:
- type: entity
  id: membership
  effect: creates
  to: Invited
permits:
- related:
  - verb: has
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: membership
    fact: Role
    is: Admin
  - entity: subscription
    fact: Status
    is: Active
- related:
  - verb: has
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can add members
    is: true
  - entity: subscription
    fact: Status
    is: Active
- actors:
  - instance-administrator
  when:
  - entity: subscription
    fact: Status
    is: Active
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: app/services/group_service.rb#invite
---

# Admins invite people to a group, and members do when the group lets them add members

Invitations also need the organization's plan to be active.
