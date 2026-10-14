---
appliesTo:
- type: entity
  id: poll
  facts:
  - Hide results
  - Vote reason
  - Closing soon reminder
  - Vote weights
- type: capability
  id: start-poll
references:
- kind: code
  role: implementation
  target: app/models/poll.rb#anonymous_invariants
- kind: code
  role: implementation
  target: app/services/poll_service.rb#build
---

# Anonymous polls hide results until closing and take no vote reasons

An anonymous poll also always reminds people who have not voted when a day remains, and never uses vote weights.
