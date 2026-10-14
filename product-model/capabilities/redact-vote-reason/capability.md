---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/stance_service.rb#redact
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
---

# Redact vote reason

Hide a vote's reason and attachments while the vote keeps counting.
