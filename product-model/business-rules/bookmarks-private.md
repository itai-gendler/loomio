---
appliesTo:
- type: entity
  id: bookmark
  effect: creates
permits:
- related:
  - verb: saves
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/bookmark.rb
---

# Bookmarks are saved, read and removed only by their owner

Saving needs being able to see the item.
