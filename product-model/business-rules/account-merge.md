---
appliesTo:
- type: entity
  id: user
  effect: removes
permits:
- self: true
references:
- kind: code
  role: implementation
  target: app/services/merge_users_service.rb
- kind: code
  role: implementation
  target: app/controllers/merge_users_controller.rb
---

# Only the person holding both accounts merges them

The person proves the account to keep by following a link sent to its address and signing in to it.
