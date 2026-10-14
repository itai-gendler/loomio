---
appliesTo:
- type: entity
  id: thread-member
  effect: changes
  facts:
  - Thread admin
permits:
- related:
  - verb: has
    entity: thread
  - verb: has
    entity: thread-member
  - verb: holds
    entity: user
  when:
  - entity: thread-member
    fact: Thread admin
    is: true
- related:
  - verb: has
    entity: thread
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
  target: app/models/ability/topic_reader.rb
---

# Only thread admins and admins make someone a thread admin

Thread admins manage one thread and its polls.
