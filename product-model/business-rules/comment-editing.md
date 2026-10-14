---
appliesTo:
- type: entity
  id: comment
  effect: changes
  facts:
  - Body
permits:
- related:
  - verb: writes
    entity: user
  when:
  - entity: group
    fact: Members can edit comments
    is: true
  - entity: thread
    fact: Locked
    is: false
- related:
  - verb: writes
    entity: user
  when:
  - entity: thread
    fact: Direct
    is: true
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
  - entity: group
    fact: Admins can edit member comments
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
  - entity: group
    fact: Admins can edit member comments
    is: true
  - entity: thread
    fact: Locked
    is: false
references:
- kind: code
  role: implementation
  target: app/models/ability/comment.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/discussions/comments/index.md
---

# Authors edit their comments where the group allows it, and admins edit others' only where the group allows that

Nobody edits comments in a locked thread. In a direct discussion authors always may edit their comments.
