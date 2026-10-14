---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses an option and writes a reason
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product records the vote, updates the results and adds the vote to the thread when it has a reason
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: changes
    from: Undecided
    to: Cast
    facts:
    - Choices
    - Reason
    - Cast at
  - entity: poll
    effect: changes
    facts:
    - Results
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::thread
---

# Vote on a proposal

## Trigger

A voter decides their position on an open proposal.

## Outcome

The vote counts in the results and, when it has a reason and results are not hidden until closing, appears in the thread.
