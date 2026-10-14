---
domain: members
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/membership_service.rb#remove_delegate
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/delegated_voters/index.md
---

# Revoke delegate

Stop a member being one of the group's delegates.
