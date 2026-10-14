---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor opens the group's address
  kind: actor
  actor: visitor
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::public::group
- text: The Product shows the group's name and description and the public threads it holds
  kind: product
  actor: visitor
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
    - Description
    - Privacy
  - entity: thread
    effect: reads
    facts:
    - Last activity
  - entity: discussion
    effect: reads
    facts:
    - Title
  contexts:
    web:
      place: web::public::group
---

# View an Open group without signing in

## Trigger

A visitor opens the address of an Open or Closed group.

## Outcome

The visitor sees the group's name and description, and the public threads of an Open group.
