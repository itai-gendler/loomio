---
appliesTo:
- type: entity
  id: comment
  effect: creates
permits:
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
  - entity: thread
    fact: Locked
    is: false
  - entity: thread
    fact: Allow comments
    is: true
- related:
  - verb: holds
    entity: thread
  - verb: has
    entity: thread-member
  - verb: holds
    entity: user
  when:
  - entity: thread-member
    fact: Guest
    is: true
  - entity: thread
    fact: Locked
    is: false
  - entity: thread
    fact: Allow comments
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/comment.rb
---

# People in a thread comment while it is unlocked and allows comments

People in a thread are the group's members and the thread's guests.
