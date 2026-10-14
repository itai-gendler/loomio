---
domain: polls
references:
- kind: code
  role: implementation
  target: app/models/stance.rb
- kind: code
  role: implementation
  target: app/services/stance_service.rb
- kind: code
  role: implementation
  target: app/models/concerns/validates_ballot.rb
- kind: code
  role: implementation
  target: app/models/ability/stance.rb
---

# Vote

One person's response to a poll that is not anonymous: the options they chose or scored and their reason. Everyone eligible holds a Vote from the moment they can vote, undecided until they cast it. A change made after a while, or after someone replied, keeps the earlier Vote in the history.

## Information kept

- **Choices** — the options chosen, scored, ranked or allocated, or none of the above
- **Reason** — why the person voted this way
- **Weight** — how much the vote counts when the poll uses vote weights
- **Cast at** — when the vote was cast
- **Invited by** — who gave the person a vote in the poll
- **Reason redacted** — whether a poll admin hid the vote's reason and attachments; the vote still counts

## States

### Undecided

The person may vote and has not yet.

### Cast

The person has voted; this is their current vote.

### Superseded

The person changed or removed their vote; this earlier vote stays in the history.

### Removed

The person can no longer vote: a poll admin removed them or they left the group while the poll was open.
