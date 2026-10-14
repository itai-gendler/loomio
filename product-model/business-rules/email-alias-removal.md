---
appliesTo:
- type: entity
  id: email-alias
  effect: removes
permits:
- related:
  - verb: recognizes
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
  target: app/controllers/api/v1/received_emails_controller.rb#destroy_alias
---

# Only admins forget an email alias

Forgetting an alias makes the address unrecognized again.
