---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens the thread
  kind: actor
  actor: visitor
  entities:
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::thread
- text: The Product shows the discussion, its comments, polls, outcomes and the results the Visitor may see
  kind: product
  actor: visitor
  entities:
  - entity: thread
    effect: reads
    facts:
    - Tags
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
  - entity: outcome
    effect: reads
    facts:
    - Statement
  contexts:
    web:
      place: web::public::thread
---

# Read a public thread without signing in

## Trigger

A visitor follows a link to a public thread.

## Outcome

The visitor reads the thread, and results of polls whose results are not hidden from them.
