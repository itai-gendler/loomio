---
appliesTo:
- type: entity
  id: outcome
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
  - entity: poll
    fact: Closed at
    present: true
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
  - entity: poll
    fact: Closed at
    present: true
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
  - entity: group
    fact: Members can edit discussions
    is: true
  - entity: poll
    fact: Closed at
    present: true
references:
- kind: code
  role: implementation
  target: app/models/ability/outcome.rb
---

# Poll admins share an outcome once voting has closed, and members do when the group lets them edit discussions

Sharing a new outcome keeps the earlier one.
