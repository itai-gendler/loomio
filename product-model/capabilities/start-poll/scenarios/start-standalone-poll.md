---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects New poll on the group's Polls tab and chooses a template
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The User enters a title, details, options and a closing time
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product opens a thread for the poll in the group and makes the User its thread admin
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: creates
    to: Active
    facts:
    - Private
    - Direct
    - Locked
    - Pinned
    - Tags
    - Reply arrangement
    - Allow comments
    - Allow reactions
    - Concurrent polls
    - Comment length limit
    - Last activity
  - entity: thread-member
    effect: creates
    to: Active
    facts:
    - Guest
    - Thread admin
    - Email notifications
    - Invited by
    with: thread
  - entity: group
    effect: reads
    facts: []
  - entity: poll
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product creates the poll open for voting, gives every member an undecided vote and notifies them that voting has opened
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
- text: The Product shows the poll in its thread
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

# Start a poll without a discussion

## Trigger

A member wants responses to a simple question without a discussion first.

## Outcome

The poll has a thread of its own in the group, the User administers it and everyone in the group holds an undecided vote.
