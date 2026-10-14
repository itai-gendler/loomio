---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration asks for a thread and its items
  kind: actor
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: api
- text: The Product returns the thread's discussion, comments, polls, votes and outcomes the User may read, in thread order
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
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
  contexts:
    web:
      place: api
---

# Read a thread through the API

## Trigger

An integration acting as a person asks for a thread's items.

## Outcome

The integration has the thread's items in order, under the same visibility as the web app.
