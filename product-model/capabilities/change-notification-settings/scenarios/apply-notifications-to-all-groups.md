---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses a setting and selects Apply to all groups
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::notification-settings
- text: The Product saves it as the default and applies it to each of the User's groups and threads
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Email notifications default
  - entity: membership
    effect: changes
    facts:
    - Email notifications
  - entity: thread-member
    effect: changes
    facts:
    - Email notifications
  - entity: thread
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::notification-settings
---

# Apply a notification setting to every group

## Trigger

A person wants the same setting in all their groups and threads.

## Outcome

Every group and thread of the person uses the chosen setting.
