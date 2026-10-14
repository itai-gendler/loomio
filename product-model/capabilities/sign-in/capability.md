---
availability:
- place: web::public
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/sessions_controller.rb
- kind: code
  role: implementation
  target: app/services/login_token_service.rb
- kind: code
  role: implementation
  target: app/controllers/identities/base_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/signing_in/index.md
---

# Sign in

Sign in to Loomio. Where the server offers its own sign-in, people choose a password, an emailed six-digit code, a passkey or an identity provider such as Google; a server that offers only its organization's single sign-on shows just that.
