---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/translation_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/translations_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/translation/index.md
---

# Translate

Show someone else's writing in one's own language. The translation comes from the translation service the server uses, on request.
