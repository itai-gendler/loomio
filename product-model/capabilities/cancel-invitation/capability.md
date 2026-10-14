---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#revoke
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/inviting_people/index.md
---

# Cancel invitation

Withdraw an invitation the invitee has not accepted yet.
