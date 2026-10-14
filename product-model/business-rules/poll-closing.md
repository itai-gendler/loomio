---
appliesTo:
- type: entity
  id: poll
  effect: changes
  to: Closed
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
- unattended: true
references:
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: code
  role: implementation
  target: app/workers/close_expired_poll_worker.rb
---

# Only poll admins close a poll early, and the Product closes it at its closing time

Closing early and closing at the closing time end voting the same way.
