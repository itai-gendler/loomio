---
appliesTo:
- type: entity
  id: user
  effect: changes
  facts:
  - Deactivated
permits:
- self: true
- actors:
  - instance-administrator
references:
- kind: code
  role: implementation
  target: app/models/ability/user.rb
---

# People deactivate or delete only their own account, and instance administrators any account

Deactivating keeps the person's name on what they wrote; deleting removes it.
