---
appliesTo:
- type: entity
  id: vote
  facts:
  - Choices
- type: entity
  id: anonymous-ballot
  facts:
  - Choices
- type: entity
  id: poll
  facts:
  - Ballot limits
references:
- kind: code
  role: implementation
  target: app/models/concerns/validates_ballot.rb
---

# A vote stays within the poll's choice, score and budget limits

Choices fall between the poll's fewest and most options, scores within its range, allocated dots within the budget, and rankings run one, two, three without gaps.
