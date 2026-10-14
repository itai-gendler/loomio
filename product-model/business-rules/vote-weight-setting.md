---
appliesTo:
- type: entity
  id: vote
  effect: changes
  facts:
  - Weight
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
    fact: Vote weights
    is: true
  - entity: poll
    fact: Closed at
    absent: true
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
    fact: Vote weights
    is: true
  - entity: poll
    fact: Closed at
    absent: true
references:
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
- kind: code
  role: implementation
  target: app/services/stance_service.rb#set_weight
---

# Only poll admins set vote weights, while the poll uses them and has not closed

Weights are zero or more with up to three decimal places; eligible voters and quorum still count people.
