---
kind: configuration
of: capability-scenario
settings:
- entity: server-settings
  fact: Local sign-in
takesEffect: 'When the sign-in page opens: the server''s configuration decides which sign-in options it offers.'
stability: Fixed for the server until its operator changes the configuration; signed-in sessions continue.
alternatives:
- id: sign-in-with-identity-provider
  selectedWhen: 'Local sign-in is Enabled: identity providers are offered beside passwords, emailed codes and passkeys, and the person chooses.'
- id: sign-in-through-single-sign-on
  selectedWhen: 'Local sign-in is Disabled: the server shows only its organization''s single sign-on.'
references:
- kind: code
  role: implementation
  target: app/extras/app_config.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/sessions_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/signing_in/index.md
---

# Sign-in methods

A server either offers its own sign-in beside identity providers, or only its organization's single sign-on.
