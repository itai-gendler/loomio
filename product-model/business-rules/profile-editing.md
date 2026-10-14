---
appliesTo:
- type: entity
  id: user
  effect: changes
  facts:
  - Name
  - Email
  - Username
  - Introduction
  - Location
  - Language
  - Time zone
  - Translate automatically
  - Email notifications default
  - Catch-up email
permits:
- self: true
references:
- kind: code
  role: implementation
  target: app/models/ability/user.rb
- kind: code
  role: implementation
  target: app/services/user_service.rb#update
---

# People change only their own profile and notification defaults

Where the organization's sign-in manages names and email addresses, those come from it.
