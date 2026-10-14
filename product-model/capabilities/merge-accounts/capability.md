---
domain: profile
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/merge_users_service.rb
- kind: code
  role: implementation
  target: app/controllers/merge_users_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/merge_accounts/index.md
---

# Merge accounts

Combine two accounts with different email addresses into the one to keep. Memberships and everything the retired account wrote move to the kept account, and the retired account is deleted.
