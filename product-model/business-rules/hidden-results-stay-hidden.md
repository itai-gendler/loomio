---
appliesTo:
- type: entity
  id: poll
  facts:
  - Hide results
  - Results
- type: capability
  id: edit-poll
references:
- kind: code
  role: implementation
  target: app/models/poll.rb#cannot_reveal_results_early
---

# Results hidden until closing are never revealed early

Once a poll hides results until it closes, that setting cannot be relaxed while it is open.
