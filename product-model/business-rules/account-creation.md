---
appliesTo:
- type: entity
  id: user
  effect: creates
permits:
- actors:
  - visitor
  when:
  - entity: server-settings
    fact: Sign-up
    is: Enabled
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/registrations_controller.rb#permission_check
---

# People create an account themselves only while sign-up is open, otherwise through an invitation

Following an invitation to an address lets that address create an account even where sign-up is closed. Every account proves control of its email address.
