---
singleton: true
references:
- kind: code
  role: implementation
  target: app/extras/app_config.rb#app_features
- kind: code
  role: implementation
  target: app/workers/destroy_group_worker.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/registrations_controller.rb#permission_check
- kind: code
  role: implementation
  target: app/services/received_email_service.rb#route
---

# Server settings

The choices the operator of a Loomio server makes for the whole server when it is deployed.

## Information kept

- **Group creation** — Enabled or Disabled; while Disabled only an instance administrator starts a top-level group
- **Automatic cleanup** — Enabled or Disabled; while Enabled the server permanently removes deleted groups once their grace period has passed
- **Local sign-in** — Enabled or Disabled; while Disabled the server offers only its organization's single sign-on
- **Sign-up** — Enabled or Disabled; while Disabled people create an account only by following an invitation
- **Threads from email** — Enabled or Disabled; whether emailing a group's address starts a discussion
