---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/groups_controller.rb#reset_token
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/inviting_people/index.md
---

# Reset shared link

Replace a group's shared link, so the old one no longer lets people join.
