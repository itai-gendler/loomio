---
kind: alternative
routes:
  web: Web
steps:
- text: The User unticks Voting opens immediately and sets an opening time before the closing time
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product creates the poll scheduled to open and gives everyone who may vote an undecided vote without notifying them yet
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: creates
    to: Scheduled
    facts:
    - Title
    - Details
    - Poll type
    - Options
    - Closing time
    - Opening time
    - Anonymous
    - Who can vote
    - Hide results
    - Vote reason
    - Reason length limit
    - Closing soon reminder
    - Notify on open
    - Quorum
    - Vote weights
    - None of the above
    - Ballot limits
    - Results
  - entity: vote
    effect: creates
    to: Undecided
    facts:
    - Weight
    - Invited by
    with: poll
  contexts:
    web:
      place: web::signed-in::poll-form
---

# Schedule a poll to open later

## Trigger

A coordinator prepares a poll ahead of an assembly.

## Outcome

The poll is visible but closed to votes until its opening time; voters will be notified when it opens.

## Edge cases

- The opening time must come before the closing time.
