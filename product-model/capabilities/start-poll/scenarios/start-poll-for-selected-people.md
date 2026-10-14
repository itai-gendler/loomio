---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Selected people only and picks voters, for example the group's delegates
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product creates the poll open for voting and gives a vote only to the people chosen
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
      place: web::signed-in::poll-form
---

# Start a poll for selected people only

## Trigger

Only some people, such as the group's delegates, should vote.

## Outcome

The poll is open and only the chosen people hold a vote.
