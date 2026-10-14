---
appliesTo:
- type: entity
  id: vote
- type: capability
  id: cast-vote
references:
- kind: code
  role: implementation
  target: app/services/stance_service.rb#update
---

# A vote changed after 15 minutes or after a reply keeps the earlier vote

Within 15 minutes of voting, and while nobody has replied, a change updates the vote in place; afterwards the earlier vote stays in the history and the new one becomes current.

## Rationale

Once others may have read or answered a position, the record of what it was is kept.
