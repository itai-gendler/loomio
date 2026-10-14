---
appliesTo:
- type: entity
  id: bookmark
  effect: reads
permits:
- related:
  - verb: saves
    entity: user
references:
- kind: code
  role: implementation
  target: app/models/ability/bookmark.rb
---

# Only the owner sees their bookmarks

Saving a bookmark notifies nobody.
