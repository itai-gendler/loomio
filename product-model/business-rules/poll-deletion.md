---
appliesTo:
- type: entity
  id: poll
  effect: changes
  to: Deleted
permits:
- related:
  - verb: holds
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
    fact: Locked
    is: false
- related:
  - verb: holds
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
  - entity: thread
    fact: Locked
    is: false
references:
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
---

# Only poll admins delete a poll, never in a locked thread

A deleted poll's votes leave the thread.
