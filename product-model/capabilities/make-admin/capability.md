---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#make_admin
- kind: code
  role: implementation
  target: app/models/ability/membership.rb
- kind: code
  role: implementation
  target: vue/src/shared/services/group_service.js
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/member_management/index.md
---

# Make admin

Give a member the admin role in a group. The new admin is notified.
