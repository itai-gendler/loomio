---
domain: profile
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/user_service.rb#redact
- kind: code
  role: implementation
  target: app/workers/redact_user_worker.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/deleting_your_account/index.md
---

# Delete account

Permanently delete one's account: the name, email address and profile are removed, the person leaves every group, and what they wrote stays without their name.
