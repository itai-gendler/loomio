---
appliesTo:
- type: entity
  id: poll
  effect: changes
  facts:
  - Results
permits:
- related:
  - verb: has
    entity: vote
  - verb: casts
    entity: user
- related:
  - verb: has
    entity: anonymous-voter
  - verb: is-listed-as
    entity: user
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
  target: app/models/poll.rb#update_counts!
---

# A poll's results change only through votes and through poll admins closing, reopening or removing voters

Each vote cast, changed or removed updates the results; closing counts an STV Election.
