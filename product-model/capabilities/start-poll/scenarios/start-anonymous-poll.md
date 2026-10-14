---
kind: alternative
routes:
  web: Web
steps:
- text: The User turns on anonymous voting
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product creates the poll open for voting with results hidden until closing, vote reasons disabled and the closing reminder going to people who have not voted, and lists everyone who may vote as an anonymous voter
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
  - entity: anonymous-voter
    effect: creates
    to: Not voted
    facts:
    - Group member
    - Invited by
    with: poll
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
---

# Start an anonymous poll

## Trigger

A coordinator needs votes nobody can connect to the people who cast them.

## Outcome

The poll is open, everyone who may vote is listed as an anonymous voter, and results stay hidden until it closes.

## Edge cases

- Count, Question and Time poll types cannot be anonymous.
- Anonymous polls never use vote weights.
