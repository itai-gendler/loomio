---
domain: group-emails
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/received_emails_controller.rb#destroy_alias
---

# Remove email alias

Forget a recognized or blocked address for a group.
