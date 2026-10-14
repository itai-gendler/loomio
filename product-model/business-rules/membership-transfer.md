---
appliesTo:
- type: entity
  id: membership
  effect: changes
  facts:
  - Person
permits:
- related:
  - verb: holds
    entity: user
references:
- kind: code
  role: implementation
  target: app/services/merge_users_service.rb
---

# A Membership moves to another account only when its person merges accounts

Where both accounts belong to the same group, the kept account's Membership remains.
