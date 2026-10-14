---
domain: group-emails
references:
- kind: code
  role: implementation
  target: app/models/received_email.rb
- kind: code
  role: implementation
  target: app/services/received_email_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/received_emails_controller.rb
---

# Unrecognized email

An email sent to a group's address from a sender the group does not recognize as a member. It waits for an admin to say whose address it is or to reject the sender.

## Information kept

- **Sender** — the From address
- **Subject** — the email's subject
- **Body** — the email's text and attachments

## States

### Waiting

It waits for an admin.

### Accepted

Its sender was recognized and it became a discussion.

### Rejected

An admin rejected its sender.
