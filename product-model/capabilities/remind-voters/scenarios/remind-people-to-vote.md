---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Remind, keeps or changes the recipients and writes an optional message
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product notifies the chosen voters
  kind: product
  actor: user
  entities:
  - entity: vote
    effect: reads
    facts:
    - Cast at
  contexts:
    web:
      place: web::signed-in::thread
---

# Remind people to vote

## Trigger

A poll admin wants more people to vote before it closes.

## Outcome

The chosen voters are notified, with the admin's message.

## Edge cases

- Reminders are offered once at least two people can vote.
