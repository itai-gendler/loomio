---
appliesTo:
- type: entity
  id: thread-member
  effect: changes
  to: Removed
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

# Only thread admins and admins remove a guest from a thread

A removed guest can no longer open the thread.
