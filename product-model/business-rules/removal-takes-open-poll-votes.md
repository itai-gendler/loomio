---
appliesTo:
- type: entity
  id: vote
- type: capability
  id: remove-from-group
- type: capability
  id: leave-group
- type: capability
  id: cancel-invitation
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#group_members_removed
- kind: code
  role: implementation
  target: app/services/membership_service.rb#restore_topic_access
---

# Leaving or being removed takes a person's votes out of the group's open polls

When someone leaves, is removed or has their invitation cancelled, their votes in the group's polls that are still open stop counting, cast or not; closed polls keep them. Their comments stay. Coming back restores their votes in polls still open.
