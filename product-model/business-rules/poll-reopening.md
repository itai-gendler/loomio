---
appliesTo:
- type: entity
  id: poll
  effect: changes
  from: Closed
  to: Open
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
  - fact: Anonymous
    is: false
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
  - fact: Anonymous
    is: false
  - entity: thread
    fact: Locked
    is: false
references:
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
---

# Only poll admins reopen a closed poll, never an anonymous one

Nobody reopens a poll in a locked thread.
