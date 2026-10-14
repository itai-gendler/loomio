---
appliesTo:
- type: entity
  id: discussion
  effect: creates
permits:
- related:
  - verb: opens
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
  - entity: user
    fact: Email verified
    is: true
- related:
  - verb: opens
    entity: thread
  - verb: holds
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can start discussions
    is: true
  - entity: user
    fact: Email verified
    is: true
- actors:
  - user
  when:
  - entity: group
    fact: Non-members can start discussions
    is: true
  - entity: group
    fact: Privacy
    is-not: Secret
  - entity: user
    fact: Email verified
    is: true
- actors:
  - user
  when:
  - entity: thread
    fact: Direct
    is: true
  - entity: user
    fact: Email verified
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/discussion.rb
---

# Admins start discussions, and members, non-members and direct participants do when allowed

In a group, admins always may; members may when the group lets them start discussions; people outside a non-secret group may when it lets non-members start discussions. A direct discussion belongs to no group. Every case needs a verified email address.
