---
kind: alternative
routes:
  web: Web
steps:
- text: The Instance administrator confirms deletion of the group
  kind: actor
  actor: instance-administrator
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product deletes the group and its subgroups and emails every admin
  kind: product
  actor: instance-administrator
  entities:
  - entity: group
    effect: changes
    from: Active
    to: Deleted
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# An instance administrator deletes a group

## Trigger

An instance administrator removes a group they do not administer.

## Outcome

The group and its subgroups are deleted and its admins have been warned.
