---
appliesTo:
- type: entity
  id: thread
  facts:
  - Concurrent polls
- type: capability
  id: start-poll
references:
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
---

# A thread runs one active poll at a time unless it allows concurrent polls

A new poll in a thread with an active poll is refused unless the thread's settings allow concurrent polls.
