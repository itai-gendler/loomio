---
domain: polls
references:
- kind: code
  role: implementation
  target: app/models/outcome.rb
- kind: code
  role: implementation
  target: app/services/outcome_service.rb
- kind: code
  role: implementation
  target: app/models/ability/outcome.rb
---

# Outcome

The statement of what was decided and what happens next, shared once a poll has closed. It appears above the poll's results.

## Information kept

- **Statement** — what was decided and what happens next
- **Review date** — when the author is reminded to review the decision
- **Chosen option** — the option the outcome settles on, such as the chosen date of a time poll
- **Event location** — where a scheduled meeting takes place

## States

### Current

The outcome shown for the poll.

### Superseded

A newer outcome replaced this one.
