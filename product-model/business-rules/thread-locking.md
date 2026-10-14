---
appliesTo:
- type: entity
  id: thread
  effect: changes
  facts:
  - Locked
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
  target: app/services/topic_service.rb#lock
- kind: code
  role: implementation
  target: vue/src/shared/services/topic_service.js
---

# Only thread admins and admins lock or unlock a thread

A thread is locked once its active polls have closed.
