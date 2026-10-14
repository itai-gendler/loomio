---
kind: alternative
routes:
  web: Web
steps:
- text: The poll asks voters to rank, score or allocate
  kind: condition
  actor: user
  entities:
  - entity: poll
    effect: reads
    facts:
    - Poll type
    - Ballot limits
  contexts:
    web:
      place: web::signed-in::thread
- text: The User ranks, scores or allocates dots to the options
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product records the vote and updates the results
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: changes
    from: Undecided
    to: Cast
    facts:
    - Choices
    - Cast at
  - entity: poll
    effect: changes
    facts:
    - Results
  contexts:
    web:
      place: web::signed-in::thread
---

# Rank, score or allocate

## Trigger

A voter responds to a poll that asks them to rank, score or allocate dots among options.

## Outcome

The ballot counts in the results.

## Edge cases

- A ranking must number its choices one, two, three without gaps.
- An STV ballot ranks at least one candidate.
