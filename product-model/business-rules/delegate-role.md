---
appliesTo:
- type: entity
  id: membership
  effect: changes
  facts:
  - Delegate
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
---

# Only admins choose a group's delegates

Delegates are the people invited when a poll is limited to a group's delegates.
