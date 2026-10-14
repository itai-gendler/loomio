---
appliesTo:
- type: entity
  id: tag
  effect: creates
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
- related:
  - verb: owns
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can create tags
    is: true
references:
- kind: code
  role: implementation
  target: app/services/tag_service.rb#can_create_tag?
---

# Admins create tags, and members do when the group lets them create tags

Tags belong to the organization; admins of the top-level group may always create them, and subgroup admins while tagging their subgroup's threads.
