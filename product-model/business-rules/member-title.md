---
appliesTo:
- type: entity
  id: membership
  effect: changes
  facts:
  - Title
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
references:
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
---

# Members set their own title, and admins set anyone's

A title shows beside the member's name in this group only.
