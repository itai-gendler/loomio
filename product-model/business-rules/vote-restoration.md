---
appliesTo:
- type: entity
  id: vote
  effect: changes
  to: Undecided
permits:
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
  - entity: subscription
    fact: Status
    is: Active
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
    fact: Members can add members
    is: true
  - entity: subscription
    fact: Status
    is: Active
- actors:
  - instance-administrator
  when:
  - entity: subscription
    fact: Status
    is: Active
references:
- kind: code
  role: implementation
  target: app/services/group_service.rb#invite
- kind: code
  role: implementation
  target: app/services/membership_service.rb#restore_topic_access
---

# Inviting a former member back restores their votes in the group's open polls

Whoever may invite the person again brings back the votes they held in polls that are still open.
