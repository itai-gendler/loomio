---
appliesTo:
- type: entity
  id: discussion-template
  effect: creates
permits:
- related:
  - verb: keeps
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
  - verb: keeps
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can create templates
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/discussion_template.rb
---

# Admins create discussion templates, and members do when the group lets them create templates

Starting a vote or discussion from a template copies it; later changes to the template do not reach what was started.
