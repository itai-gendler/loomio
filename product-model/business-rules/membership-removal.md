---
appliesTo:
- type: entity
  id: membership
  effect: changes
  to: Removed
permits:
- related:
  - verb: holds
    entity: user
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
- related:
  - verb: invites
    entity: user
  when:
  - state: Invited
- actors:
  - instance-administrator
references:
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
- kind: code
  role: implementation
  target: app/services/membership_service.rb#revoke
---

# People leave a group themselves, admins remove members, and inviters cancel their own pending invitations

Instance administrators may remove anyone. Removal applies to the group's subgroups as well.
