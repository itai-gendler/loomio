---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to remove a voter in Manage voters and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product removes the person's vote, earlier versions included, and updates the results
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: changes
    from: Cast
    to: Removed
    facts: []
  - entity: poll
    effect: changes
    facts:
    - Results
  contexts:
    web:
      place: web::signed-in::thread
---

# Remove a voter

## Trigger

A poll admin decides someone should not be eligible to vote.

## Outcome

The person can no longer vote and their vote no longer counts.
