---
kind: alternative
routes:
  web: Web
steps:
- text: The User gives the draft a closing time
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-form
- text: The Product opens the poll for voting and notifies the voters when set to
  kind: product
  actor: user
  entities:
  - entity: poll
    effect: changes
    from: Draft
    to: Open
    facts:
    - Closing time
  contexts:
    web:
      place: web::signed-in::poll-form
---

# Open a draft poll

## Trigger

A coordinator finishes a draft and gives it a closing time.

## Outcome

Voting is open and the voters are notified when set to.
