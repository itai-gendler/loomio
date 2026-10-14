---
appliesTo:
- type: entity
  id: membership
  effect: changes
  facts:
  - Role
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
- related:
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Admin count
    is: 0
- actors:
  - instance-administrator
references:
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
- kind: code
  role: implementation
  target: vue/src/shared/services/group_service.js
---

# Admins make and demote admins, and a member may become admin of a group that has none

An admin of a parent group may also make themselves admin of a subgroup they belong to, and anyone may step down from the admin role. Instance administrators may demote anyone.
