---
kind: alternative
routes:
  web: Web
steps:
- text: The User leaves the closing time empty and does not open voting
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product saves the poll as a draft
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: creates
    to: Draft
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

# Save a poll as a draft

## Trigger

A coordinator starts preparing a poll without deciding when it runs.

## Outcome

The poll exists as a draft that nobody can vote in.
