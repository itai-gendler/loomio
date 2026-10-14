---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Visible to parent group or Secret as the group's privacy
  kind: actor
  actor: user
  entities:
  - entity: group
    as: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group-settings
- text: The Product saves the privacy, makes discussions private only and, for Secret, makes joining by invitation only
  kind: product
  actor: user
  entities:
  - entity: group
    as: group
    effect: changes
    facts:
    - Privacy
    - Discussion privacy
    - How people join
    - Listed in directory
  - entity: discussion
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group-settings
- text: The Product makes every thread in the group and its subgroups private and makes public subgroups visible to parent group members only
  kind: product
  actor: user
  entities:
  - entity: thread
    effect: changes
    facts:
    - Private
  - entity: group
    as: subgroup
    effect: changes
    facts:
    - Privacy
    - Discussion privacy
  contexts:
    web:
      place: web::signed-in::group-settings
---

# Hide a group from the public

## Trigger

An admin of an Open or Closed group decides only invited people should find it.

## Outcome

The group and its threads are private, and its public subgroups are visible to parent members only.
