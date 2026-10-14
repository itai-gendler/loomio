---
appliesTo:
- type: entity
  id: email-alias
  effect: creates
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
  target: app/controllers/api/v1/received_emails_controller.rb
---

# Only admins recognize, block or forget an email sender for a group

A recognized alias lets later emails from the address start discussions as its member.
