---
kind: primary
routes:
  web: Web
steps:
- text: The grace period since the group was deleted has passed and automatic cleanup is enabled
  kind: condition
  unattended: true
  entities:
  - entity: server-settings
    effect: reads
    facts:
    - Automatic cleanup
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in
- text: The Product permanently removes the group with everything in it
  kind: product
  entities:
  - entity: group
    effect: removes
    from: Deleted
  contexts:
    web:
      place: web::signed-in
---

# A deleted group is permanently removed

## Trigger

The grace period after a group's deletion passes.

## Outcome

The group and everything in it are gone for good.

## Edge cases

- A group restored and deleted again starts a new grace period.
