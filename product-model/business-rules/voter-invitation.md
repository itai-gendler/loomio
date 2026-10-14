---
appliesTo:
- type: entity
  id: vote
  effect: creates
  to: Undecided
permits:
- related:
  - verb: has
    entity: poll
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
  - verb: has
    entity: poll
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
  target: app/services/poll_service.rb#group_members_added
---

# Only poll admins give people a vote, and the Product gives newcomers one

People who join the group, or become guests of the thread, while a poll open to everyone has not closed receive a vote automatically.
