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
      place: web::signed-in::discussion-template-form
- text: The Product saves the template for the group
  kind: product
  actor: user
  entities:
  - entity: discussion-template
    effect: creates
    to: Visible
    facts:
    - Title
    - Subtitle
    - Help
    - Starts direct discussions
    - Default title
    - Context
    - Tags
    - Invite everyone
    - Suggested poll templates
    - Thread settings
    - Position
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::discussion-template-form
---

# Create a discussion template

## Trigger

An admin, or a member where the group lets members create templates, sets up a reusable discussion.

## Outcome

The template is offered to people starting a discussion in the group.
