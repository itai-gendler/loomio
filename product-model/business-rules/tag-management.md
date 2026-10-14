---
appliesTo:
- type: entity
  id: tag
  effect: changes
permits:
- related:
  - verb: owns
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
  target: app/models/ability/tag.rb
---

# Only admins of the organization rename, recolor or delete its tags

Changes apply throughout the organization, including its subgroups.
