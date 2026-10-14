---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the dashboard
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::dashboard
- text: The Product lists recent threads the User may read and the open polls where the User has not voted
  kind: product
  actor: user
  entities:
  - entity: discussion
    effect: reads
    facts:
    - Title
  - entity: thread
    effect: reads
    facts:
    - Last activity
  - entity: poll
    effect: reads
    facts:
    - Title
    - Closing time
  - entity: vote
    effect: reads
    facts:
    - Cast at
  contexts:
    web:
      place: web::signed-in::dashboard
---

# Open the dashboard

## Trigger

A person signs in or returns to Loomio.

## Outcome

The person sees recent activity across their groups and what needs their vote.
