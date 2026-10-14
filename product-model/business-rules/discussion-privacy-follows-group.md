---
appliesTo:
- type: entity
  id: thread
  facts:
  - Private
- type: capability
  id: start-discussion
- type: capability
  id: edit-group-settings
references:
- kind: code
  role: implementation
  target: app/models/topic.rb#privacy_is_permitted_by_group
- kind: code
  role: implementation
  target: app/services/group_service/privacy_change.rb
---

# A thread's privacy follows the group's discussion privacy

A group allowing public discussions only holds public threads, one allowing private only holds private threads, and a direct thread is always private. Changing the group's discussion privacy changes its existing threads.
