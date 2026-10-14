---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#revoke
- kind: code
  role: implementation
  target: vue/src/shared/services/group_service.js
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/member_management/index.md
---

# Leave group

Leave a group, with the same effect as being removed from it.
