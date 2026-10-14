---
appliesTo:
- type: entity
  id: thread-member
  effect: creates
permits:
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
  - entity: subscription
    fact: Guests allowed
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
  - entity: group
    fact: Members can add guests
    is: true
  - entity: subscription
    fact: Guests allowed
    is: true
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
  - entity: thread
    fact: Direct
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/topic.rb
- kind: code
  role: implementation
  target: app/services/topic_service.rb#add_readers
---

# Admins invite guests into a thread, and members do when the group lets them, while the plan allows guests

In a direct discussion the thread admins invite guests.
