---
domain: profile
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/user_service.rb#update
- kind: code
  role: implementation
  target: app/models/ability/user.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/users/user_profile/index.md
- kind: doc
  role: intent
  target: docs/en/user_manual/users/translation/index.md
---

# Edit profile

Change one's own name, email address, username, introduction, location, language, time zone and whether content is translated automatically.
