---
domain: polls
references:
- kind: code
  role: implementation
  target: app/models/anonymous_ballot.rb
- kind: code
  role: implementation
  target: app/services/anonymous_ballot_service.rb
---

# Anonymous ballot

A vote submitted in an anonymous poll, kept with no name, time, reason or link to who submitted it. It cannot be retrieved, changed or withdrawn.

## Information kept

- **Choices** — the options chosen, scored or ranked
- **None of the above** — whether the ballot chose none of the options
