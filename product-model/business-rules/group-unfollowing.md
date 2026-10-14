---
appliesTo:
- type: entity
  id: group-follow
  effect: removes
permits:
- related:
  - verb: follows-with
    entity: user
references:
- kind: code
  role: implementation
  target: app/services/group_follow_service.rb#destroy
---

# Only the follower stops following a group

Stopping leaves the group out of the follower's catch-up.
