---
type: messaging
actors:
- user
entryPoints:
- messaging: '{group-handle}@{reply-host}'
references:
- kind: code
  role: implementation
  target: app/mailboxes/received_email_mailbox.rb
- kind: code
  role: implementation
  target: app/services/received_email_service.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/email/index.md
---

# Email

Email people send to Loomio: replies to notification emails, which become comments, and messages to a group's address, which start discussions.
