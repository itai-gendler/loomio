---
appliesTo:
- type: entity
  id: comment
  effect: changes
  to: Visible
permits:
- related:
  - verb: writes
    entity: user
  when:
  - entity: thread
    fact: Locked
    is: false
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
  target: app/models/ability/comment.rb
---

# The author who discarded a comment, or a thread admin, restores it

An author restores only a comment they discarded themselves.
