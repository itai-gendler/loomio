---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#remind
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/inviting_people/index.md
---

# Remind voters

Send a reminder to people invited to vote in an open poll, by default everyone invited.
