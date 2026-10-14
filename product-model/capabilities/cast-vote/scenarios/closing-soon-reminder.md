---
kind: primary
routes:
  web: Web
steps:
- text: A day remains before the poll closes
  kind: condition
  unattended: true
  entities:
  - entity: poll
    effect: reads
    facts:
    - Closing soon reminder
    - Closing time
  contexts:
    web:
      place: web::signed-in::thread
- text: The Product reminds the people the poll's reminder setting names; an anonymous poll lasting a day or more reminds everyone who has not voted
  kind: product
  entities:
  - entity: poll
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::signed-in::thread
---

# Voters are reminded before closing

## Trigger

A day remains before a poll closes.

## Outcome

The people the reminder setting names are reminded to vote.
