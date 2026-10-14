---
kind: primary
routes:
  web: Web
steps:
- text: The User enters search words, optionally limited to a group or organization
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::search
- text: The Product shows matching discussions, comments, polls, votes and outcomes from threads the User may read
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts:
    - Title
  - entity: comment
    effect: reads
    facts:
    - Body
  - entity: poll
    effect: reads
    facts:
    - Title
  - entity: vote
    effect: reads
    facts:
    - Reason
  - entity: outcome
    effect: reads
    facts:
    - Statement
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::search
---

# Search

## Trigger

Someone looks for an earlier decision.

## Outcome

The person sees matching items they may read, with the matching words highlighted.

## Edge cases

- Votes in polls hiding results until closing, and redacted reasons, are not found.
