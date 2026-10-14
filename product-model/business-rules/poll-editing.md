---
appliesTo:
- type: entity
  id: poll
  effect: changes
  facts:
  - Title
  - Details
  - Options
  - Closing time
  - Opening time
  - Who can vote
  - Hide results
  - Vote reason
  - Reason length limit
  - Closing soon reminder
  - Notify on open
  - Quorum
  - Vote weights
  - None of the above
  - Ballot limits
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
  - fact: Closed at
    absent: true
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
  - fact: Closed at
    absent: true
  - entity: thread
    fact: Locked
    is: false
references:
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
---

# Only poll admins edit a poll, and only until it closes

Poll admins are the thread's admins and the group's admins. Nobody edits a poll in a locked thread.
