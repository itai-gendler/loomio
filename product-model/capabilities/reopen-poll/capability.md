---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#reopen
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/intro_to_decisions/index.md
---

# Reopen poll

Reopen a closed poll with a new closing time so people keep voting. Anonymous polls cannot be reopened.
