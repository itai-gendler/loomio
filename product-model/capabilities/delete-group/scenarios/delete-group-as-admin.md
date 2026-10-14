---
kind: primary
routes:
  web: Web
steps:
- text: The User confirms deletion by typing the group's handle or name
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product deletes the group and its subgroups and emails every admin that it will be permanently removed after the grace period
  kind: product
  actor: user
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

# An admin deletes a group

## Trigger

An admin decides the group is no longer needed.

## Outcome

The group and its subgroups are deleted and every admin has been warned when permanent removal will happen.

## Edge cases

- Group data can be exported only until the group is deleted.
- Restoring a deleted group happens only in the server's own administration.
