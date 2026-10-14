---
appliesTo:
- type: entity
  id: group
  effect: changes
  to: Deleted
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
- actors:
  - instance-administrator
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: app/services/group_service.rb#warn_and_discard
---

# Only admins and Instance administrators delete a group

Deleting a group also deletes its subgroups.
