---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Start a vote and chooses a proposal template
  kind: actor
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User enters a title, details, options and a closing time, keeping voting open immediately
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product creates the proposal open for voting, gives everyone in the thread an undecided vote and notifies them that voting has opened
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
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product shows the proposal in the thread
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts: []
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Start a proposal in a discussion

## Trigger

A participant wants the group to respond to a proposal after discussing it.

## Outcome

The proposal is open in the thread, everyone in the thread holds an undecided vote and has been notified that voting has opened.
