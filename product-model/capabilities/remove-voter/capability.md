---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/controllers/api/v1/stances_controller.rb#revoke
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/settings/index.md
---

# Remove voter

Take someone's vote in a poll away so they can no longer vote and their vote no longer counts.
