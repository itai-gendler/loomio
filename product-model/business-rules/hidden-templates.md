---
appliesTo:
- type: entity
  id: group
  effect: changes
  facts:
  - Hidden templates
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
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/poll_templates_controller.rb#hide
---

# Only admins hide or unhide a group's built-in poll templates

Built-in templates are shipped with Loomio and can be hidden but not deleted.
