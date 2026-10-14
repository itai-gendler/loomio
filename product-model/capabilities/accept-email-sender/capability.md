---
domain: group-emails
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/received_emails_controller.rb#allow
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/email/index.md
---

# Accept email sender

Tell a group whose address an unrecognized email came from, so it becomes a discussion and later emails from that address are accepted.
