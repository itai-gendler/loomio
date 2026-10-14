---
domain: polls
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#update
- kind: code
  role: implementation
  target: app/models/poll.rb
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/settings/index.md
- kind: code
  role: implementation
  target: app/controllers/api/b2/polls_controller.rb
---

# Edit poll

Change a poll's content and settings while it has not closed. Anonymity and the poll type never change.
