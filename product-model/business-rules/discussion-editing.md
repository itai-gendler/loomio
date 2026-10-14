---
appliesTo:
- type: entity
  id: discussion
  effect: changes
permits:
- related:
  - verb: starts
    entity: user
- related:
  - verb: opens
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
  - verb: opens
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
- related:
  - verb: opens
    entity: thread
  - verb: holds
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can edit discussions
    is: true
- related:
  - verb: opens
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
    fact: Direct
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
---

# Authors, thread admins and admins edit a discussion, and members do when the group lets them

In a direct discussion everyone in it may edit the discussion.
