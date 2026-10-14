---
appliesTo:
- type: entity
  id: thread
  effect: changes
  facts:
  - Pinned
permits:
- related:
  - verb: has
    entity: thread-member
  - verb: holds
    entity: user
  when:
  - entity: thread-member
    fact: Thread admin
    is: true
- related:
  - verb: holds
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: membership
    fact: Role
    is: Admin
references:
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: code
  role: implementation
  target: app/services/topic_service.rb#pin
---

# Only thread admins and admins pin or unpin a thread

Pinned threads appear above the group's other threads.
