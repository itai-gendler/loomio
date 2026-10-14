---
appliesTo:
- type: entity
  id: membership
  effect: changes
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

# Admins invite former members back, and members do when the group lets them add members

Inviting a former member reuses their earlier Membership as a fresh invitation with the member role.
