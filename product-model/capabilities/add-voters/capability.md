---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#invite
- kind: code
  role: implementation
  target: app/services/poll_service.rb#group_members_added
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/inviting_people/index.md
---

# Add voters

Give more people a vote in a poll from Manage voters, choosing people, groups or the group's delegates, and optionally notify them.
