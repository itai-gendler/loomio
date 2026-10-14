---
domain: group-emails
references:
- kind: code
  role: implementation
  target: app/models/member_email_alias.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/received_emails_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/email/index.md
---

# Email alias

An extra email address a group recognizes for one of its members, or a sender address the group blocks.

## Information kept

- **Address** — the email address
- **Member** — the member it belongs to; absent when the address is blocked
- **Added by** — the admin who decided
