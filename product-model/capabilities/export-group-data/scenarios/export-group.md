---
kind: primary
routes:
  web: Web
steps:
- text: The User selects Export group data and chooses CSV, HTML or JSON
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product prepares the export of the group and the subgroups the User belongs to, and emails the User a link valid for a week
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  - entity: membership
    effect: reads
    facts:
    - Role
  - entity: thread
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Export group data

## Trigger

An admin wants a backup of the group or to audit its members.

## Outcome

The admin receives an email with a link to the file.

## Edge cases

- An anonymous poll is exported only after it closes.
- Admins of an organization also export its subgroups that are not secret.
