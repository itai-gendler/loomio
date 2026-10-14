---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the thread
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product shows the thread from the first item new to the User, with comments, polls, votes, outcomes and the results the User may see
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts:
    - Tags
    - Locked
  - entity: discussion
    effect: reads
    facts:
    - Title
    - Context
  - entity: comment
    effect: reads
    facts:
    - Body
  - entity: poll
    effect: reads
    facts:
    - Title
    - Details
    - Options
    - Results
  - entity: vote
    effect: reads
    facts:
    - Choices
    - Reason
  - entity: outcome
    effect: reads
    facts:
    - Statement
    - Review date
  contexts:
    web:
      place: web::signed-in::thread
---

# Read a thread as a member

## Trigger

A member or guest opens a thread.

## Outcome

The reader sees everything in the thread they may see and lands at what is new to them.

## Edge cases

- Comments under a poll whose results are hidden until voting stay hidden from people who have not voted.
