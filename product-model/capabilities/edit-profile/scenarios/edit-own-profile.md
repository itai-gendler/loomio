---
kind: primary
routes:
  web: Web
steps:
- text: The User changes their name, username, introduction, location, language or time zone
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::profile
- text: The Product saves the profile
  kind: product
  actor: user
  entities:
  - entity: user
    effect: changes
    facts:
    - Name
    - Username
    - Introduction
    - Location
    - Language
    - Time zone
  contexts:
    web:
      place: web::signed-in::profile
---

# Edit your profile

## Trigger

A person wants others to recognize them, or wants Loomio in another language.

## Outcome

The profile shows the new details everywhere the person appears.

## Edge cases

- Where the organization's sign-in manages names and email addresses, those fields cannot be edited.
