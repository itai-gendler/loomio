---
appliesTo:
- type: entity
  id: bookmark
  effect: removes
permits:
- related:
  - verb: saves
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/bookmark.rb
---

# Only the owner removes a bookmark

Removing a bookmark affects only the owner's list.
