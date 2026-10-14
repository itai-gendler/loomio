---
appliesTo:
- type: entity
  id: comment
  effect: changes
  facts:
  - Replies
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
  target: app/models/comment.rb
---

# Replies are counted on the comment they answer as people in the thread reply

Anyone who may comment in the thread may reply.
