---
appliesTo:
- type: entity
  id: unrecognized-email
  effect: changes
permits:
- related:
  - verb: holds-for-review
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
  target: app/controllers/api/v1/received_emails_controller.rb
---

# Only admins decide what happens to an unrecognized email

An accepted email becomes a discussion; a rejected one is dropped.
