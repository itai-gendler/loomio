---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses a default email setting and a catch-up schedule
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::notification-settings
- text: The Product saves the settings
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Email notifications default
    - Catch-up email
  contexts:
    web:
      place: web::signed-in::notification-settings
---

# Change default notifications and catch-up

## Trigger

A person wants fewer or more emails.

## Outcome

Groups the person joins from now on start with the chosen setting, and the catch-up follows the new schedule.
