---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#revoke_by_id
- kind: code
  role: implementation
  target: app/services/poll_service.rb#group_members_removed
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/member_management/index.md
---

# Remove from group

Remove someone from a group and all of its subgroups. Their comments stay where they are; their votes leave the group's polls that are still open, while closed polls keep them.
