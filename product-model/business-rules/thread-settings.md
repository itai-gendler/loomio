---
appliesTo:
- type: entity
  id: thread
  effect: changes
  facts:
  - Reply arrangement
  - Allow comments
  - Allow reactions
  - Concurrent polls
  - Comment length limit
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
  target: app/services/topic_service.rb#update
---

# Only thread admins and admins change a thread's settings

Thread settings apply to everyone in the thread.
