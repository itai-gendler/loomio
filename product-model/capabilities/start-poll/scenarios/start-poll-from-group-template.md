---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses one of the group's own templates
  kind: actor
  actor: user
  entities:
  - entity: poll-template
    effect: reads
    facts:
    - Title
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User reviews the copied title, details, options and settings and sets a closing time
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product creates the poll open for voting and gives everyone in the thread an undecided vote
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
---

# Start a poll from the group's own template

## Trigger

A member starts a vote from a template the group made.

## Outcome

The new poll starts with the template's content and settings, which the member may change first.
