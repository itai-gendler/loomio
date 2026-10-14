---
domain: group-settings
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/group_service.rb#warn_and_discard
- kind: code
  role: implementation
  target: app/models/group.rb#discard!
- kind: code
  role: implementation
  target: app/workers/destroy_group_worker.rb
- kind: code
  role: implementation
  target: vue/src/shared/services/group_service.js
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/deleting_your_group/index.md
---

# Delete group

Delete a group together with its subgroups. Every admin is warned by email, nobody can open the group any more, and it is permanently removed once the server's grace period has passed.
