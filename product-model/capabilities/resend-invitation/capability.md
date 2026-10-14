---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#resend
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/inviting_people/index.md
---

# Resend invitation

Send a pending invitation again.
