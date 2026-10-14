---
appliesTo:
- type: entity
  id: vote
  effect: changes
  facts:
  - Choices
  - Reason
permits:
- related:
  - verb: casts
    entity: user
  when:
  - entity: user
    fact: Deactivated
    is: false
references:
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
---

# Each person casts and changes only their own vote, while their account is active

Voting happens only while the poll is open, and only by people who hold a vote; in a group's poll the voter must still belong to the group or be a guest of the thread.
