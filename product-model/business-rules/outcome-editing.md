---
appliesTo:
- type: entity
  id: outcome
  effect: changes
  facts:
  - Statement
  - Review date
  - Chosen option
  - Event location
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

# Poll admins edit an outcome, and members do when the group lets them edit discussions

Every version of an outcome is kept.
