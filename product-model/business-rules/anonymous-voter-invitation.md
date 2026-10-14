---
appliesTo:
- type: entity
  id: anonymous-voter
  effect: creates
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
  target: app/services/poll_service.rb#create_anonymous_poll_voters
---

# Only poll admins add anonymous voters, and the Product adds newcomers

Anonymous voters are added only while the poll is open.
