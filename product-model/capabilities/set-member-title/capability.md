---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#update
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/member_management/index.md
---

# Set title

Set the title shown beside a member's name in one group, such as their role or the organization they represent.
