---
kind: primary
routes:
  web: Web
steps:
- text: The User selects New template, starts from an example or blank, and fills in the template
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::poll-template-form
- text: The Product saves the template for the group
  kind: product
  actor: user
  entities:
  - entity: poll-template
    effect: creates
    to: Visible
    facts:
    - Title
    - Subtitle
    - Help
    - Poll type
    - Example content
    - Options
    - Default settings
    - Position
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::poll-template-form
---

# Create a poll template

## Trigger

An admin, or a member where the group lets members create templates, sets up a reusable poll.

## Outcome

The template is offered to people starting a poll in the group.
