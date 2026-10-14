---
domain: group-emails
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/received_emails_controller.rb#block
---

# Block email sender

Reject an unrecognized email and every later email from its address to the group.
