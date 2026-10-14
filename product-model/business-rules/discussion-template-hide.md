---
appliesTo:
- type: entity
  id: discussion-template
  effect: changes
  to: Hidden
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
  - verb: authors
    entity: user
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/discussion_templates_controller.rb
---

# Only admins and the template's author hide a discussion template

Built-in templates are never deleted.
