---
appliesTo:
- type: entity
  id: poll-template
  effect: changes
  to: Deleted
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
  target: app/controllers/api/v1/poll_templates_controller.rb
---

# Only admins and the template's author delete a poll template

Built-in templates are never deleted.
