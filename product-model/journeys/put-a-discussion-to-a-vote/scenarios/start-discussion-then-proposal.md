---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User writes a title and context and picks people to notify
  kind: actor
  capability: start-discussion
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product creates the discussion in its own thread and makes the User its thread admin
  kind: product
  capability: start-discussion
  actor: user
  entities:
  - entity: discussion
    effect: creates
    facts:
    - Title
    - Context
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
    with: discussion
  - entity: thread-member
    effect: creates
    to: Active
    facts:
    - Guest
    - Thread admin
    - Email notifications
    - Invited by
    with: thread
  contexts:
    web:
      place: web::signed-in::discussion-form
- text: The Product opens the new thread
  kind: product
  capability: start-discussion
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User selects Start a vote and chooses a proposal template
  kind: actor
  capability: start-poll
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The User enters a title, details, options and a closing time
  kind: actor
  capability: start-poll
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product creates the proposal open for voting and gives everyone in the thread an undecided vote
  kind: product
  capability: start-poll
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

# Start a discussion, then a proposal in it

## Trigger

A member wants context and conversation before the group responds.

## Outcome

The thread holds the discussion and an open proposal.
