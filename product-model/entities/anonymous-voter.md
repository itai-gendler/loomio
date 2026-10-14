---
domain: polls
references:
- kind: code
  role: implementation
  target: app/models/anonymous_poll_voter.rb
- kind: code
  role: implementation
  target: app/services/anonymous_ballot_service.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/polls/anonymous_voting/index.md
---

# Anonymous voter

A person's place in the electorate of an anonymous poll. It records that they may vote and whether they have, and nothing about what they chose.

## Information kept

- **Group member** — whether the person belonged to the group when they were added
- **Invited by** — who added the person to the electorate

## States

### Not voted

The person may still vote.

### Voted

The person has submitted their ballot.
