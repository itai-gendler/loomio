---
domain: polls
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/poll_service.rb#create
- kind: code
  role: implementation
  target: app/services/poll_service.rb#build
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: code
  role: implementation
  target: config/poll_types.yml
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/intro_to_decisions/index.md
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/settings/index.md
- kind: code
  role: implementation
  target: app/controllers/api/b2/polls_controller.rb
---

# Start proposal or poll

Start a proposal or poll inside a discussion's thread, or on its own in a group's own new thread. The template chosen sets the poll type, options and settings; the closing time and opening choice decide whether it opens now, opens later or stays a draft. Everyone who may vote holds an undecided vote, or a place among an anonymous poll's voters, from the start.
