---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a poll type, title, options and closing time
  kind: actor
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product creates the poll open for voting and gives everyone who may vote an undecided vote
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: creates
    to: Open
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
      place: api
---

# Start a poll through the API

## Trigger

An integration acting as a person starts a poll in a group or discussion.

## Outcome

The poll is open in its thread as if started in the web app.
