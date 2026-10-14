---
appliesTo:
- type: entity
  id: tag
  effect: removes
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

# Only admins of the organization delete its tags

Deleting a tag removes it from every thread and poll in the organization.
