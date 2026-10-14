---
appliesTo:
- type: entity
  id: anonymous-ballot
- type: capability
  id: cast-vote
references:
- kind: code
  role: implementation
  target: app/models/anonymous_ballot.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/anonymous_voting/index.md
---

# An anonymous ballot is never retrieved, changed or withdrawn

Nothing links a ballot to the person who submitted it, so nobody, coordinators and administrators included, can find, change or remove it.
