---
kind: alternative
routes:
  web: Web
steps:
- text: The User picks Public only as the privacy for the group's conversations
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group-settings
- text: The Product saves the setting and makes every thread in the group public
  kind: product
  actor: user
  entities:
  - entity: group
    effect: changes
    facts:
    - Discussion privacy
  - entity: thread
    effect: changes
    facts:
    - Private
  contexts:
    web:
      place: web::signed-in::group-settings
---

# Require public discussions

## Trigger

An admin of an Open group wants every discussion readable by anyone.

## Outcome

Every existing thread in the group is public and new ones will be too.
