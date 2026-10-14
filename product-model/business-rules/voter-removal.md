---
appliesTo:
- type: entity
  id: vote
  effect: changes
  to: Removed
  contexts:
  - place: web::signed-in::thread
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
references:
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/stances_controller.rb#revoke
---

# Only poll admins remove a voter from a poll

A removed voter's vote stops counting.
