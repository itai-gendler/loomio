---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses to start a subgroup of an organization they belong to and enters its name and privacy
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::start-group
- text: The User is an admin of the parent group, or its members can create subgroups
  kind: condition
  actor: user
  entities:
  - entity: group
    as: parent
    effect: reads
    facts:
    - Members can create subgroups
  contexts:
    web:
      place: web::signed-in::start-group
- text: The Product creates the subgroup inside the parent group and makes the User its first admin
  kind: product
  actor: user
  entities:
  - entity: group
    as: subgroup
    effect: creates
    to: Active
    facts:
    - Name
    - Handle
    - Description
    - Privacy
    - Discussion privacy
    - How people join
    - Joining prompt
    - Listed in directory
    - Parent members can see discussions
    - Members can add members
    - Members can add guests
    - Members can announce
    - Members can start discussions
    - Non-members can start discussions
    - Members can edit discussions
    - Members can edit comments
    - Members can delete comments
    - Members can start polls
    - Members can create subgroups
    - Members can create tags
    - Members can create templates
    - Admins can edit member comments
    - Admin count
    - Parent group
  - entity: membership
    effect: creates
    to: Active
    facts:
    - Role
    - Delegate
    - Vote weight
    - Accepted at
    with: subgroup
  contexts:
    web:
      place: web::signed-in::start-group
- text: The Product opens the new subgroup's page
  kind: product
  actor: user
  entities:
  - entity: group
    as: subgroup
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::group
---

# Start a subgroup

## Trigger

A member of an organization wants a separate space for a team inside it.

## Outcome

The subgroup exists inside the organization with its creator as admin.

## Edge cases

- A subgroup of a group hidden from the public cannot itself be visible to the public.
