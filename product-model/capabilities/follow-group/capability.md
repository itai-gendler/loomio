---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/group_follow_service.rb#create
- kind: code
  role: implementation
  target: app/models/ability/group.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/settings/privacy.md
---

# Follow group

Include an Open group one has not joined in one's catch-up email.
