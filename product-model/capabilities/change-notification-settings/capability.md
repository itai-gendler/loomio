---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/user_service.rb#set_volume
- kind: code
  role: implementation
  target: app/services/digest_service.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/email_settings/index.md
---

# Change notification settings

Choose the default email notifications for groups one joins and how often the catch-up email arrives.
