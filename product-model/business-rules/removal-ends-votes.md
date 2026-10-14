---
appliesTo:
- type: entity
  id: vote
  effect: changes
  to: Removed
  contexts:
  - place: web::signed-in::group
  - place: web::signed-in::profile
permits:
- related:
  - verb: casts
    entity: user
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
- actors:
  - instance-administrator
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#group_members_removed
---

# Leaving, being removed or losing an invitation removes the person's votes in the group's open polls

This happens on the group page as part of the Membership ending: the person themselves, an admin, the inviter of a pending invitation, or an instance administrator ends it. Deactivating or deleting one's own account removes only the votes not yet cast.
