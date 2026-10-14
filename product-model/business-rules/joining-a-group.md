---
appliesTo:
- type: entity
  id: membership
  effect: creates
  to: Active
permits:
- related:
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: How people join
    is: Join without approval
  - entity: user
    fact: Email verified
    is: true
- related:
  - verb: has
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: membership
    fact: Role
    is: Admin
- related:
  - verb: has
    entity: group
  - verb: has
    entity: membership
  - verb: holds
    entity: user
  when:
  - entity: group
    fact: Members can add members
    is: true
references:
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: code
  role: implementation
  target: app/services/membership_service.rb#join_group
---

# People join a group themselves only where it lets them join without approval

Otherwise a Membership becomes active when an admin, or a member allowed to add members, approves a request. Admins of a parent group may also join its subgroups that are not secret. Joining needs a verified email address and an active account.
