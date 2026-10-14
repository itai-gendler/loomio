---
appliesTo:
- type: entity
  id: poll
  facts:
  - Anonymous
  - Poll type
- type: capability
  id: edit-poll
references:
- kind: code
  role: implementation
  target: app/models/poll.rb
---

# A poll's anonymity and voting method never change after it is created

An anonymous poll's ballot settings also stay as they are once anyone has voted.
