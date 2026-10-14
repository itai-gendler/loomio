---
appliesTo:
- type: entity
  id: thread
  effect: changes
  to: Deleted
permits:
- related:
  - verb: opens
    entity: discussion
  - verb: starts
    entity: user
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
  target: app/models/ability/discussion.rb
---

# Only the author, thread admins and admins delete a discussion

Deleting a discussion deletes its thread and every poll in it.
