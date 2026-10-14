---
appliesTo:
- type: entity
  id: thread-member
  effect: changes
  facts:
  - Guest
permits:
- related:
  - verb: holds
    entity: user
- related:
  - verb: has
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
- actors:
  - instance-administrator
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#revoke_by_id
---

# Leaving or being removed from a group ends the person's guest access to its threads

People leave themselves, admins remove members, and Instance administrators remove anyone; the person's guest access to the group's threads ends with the Membership.
