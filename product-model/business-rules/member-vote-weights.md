---
appliesTo:
- type: entity
  id: membership
  effect: changes
  facts:
  - Vote weight
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
references:
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
- kind: code
  role: implementation
  target: app/services/membership_service.rb#set_weights
---

# Only admins set members' vote weights

A member's weight is copied into polls they are added to; changing it later does not change polls that already have it.
