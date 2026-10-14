---
appliesTo:
- type: entity
  id: poll-template
  effect: changes
  facts:
  - Title
  - Subtitle
  - Help
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
  when:
  - entity: group
    fact: Members can create templates
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/poll_template.rb
---

# Admins edit any poll template, and authors their own when the group lets members create templates

Only what is started afterwards uses the change.
