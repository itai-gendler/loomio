---
appliesTo:
- type: entity
  id: thread-member
  effect: changes
  facts:
  - Email notifications
permits:
- related:
  - verb: holds
    entity: user
references:
- kind: code
  role: implementation
  target: app/services/topic_service.rb#update_reader
---

# People choose only their own notification settings for a thread

A thread setting overrides the group setting for that thread only.
