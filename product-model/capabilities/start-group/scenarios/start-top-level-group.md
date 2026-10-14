---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a name, handle, description and privacy for the new group
  kind: actor
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::start-group
- text: Group creation is enabled on the server
  kind: condition
  actor: user
  entities:
  - entity: server-settings
    effect: reads
    facts:
    - Group creation
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::start-group
- text: The Product creates the group and makes the User its first admin
  kind: product
  actor: user
  entities:
  - entity: group
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
  - entity: membership
    effect: creates
    to: Active
    facts:
    - Role
    - Delegate
    - Vote weight
    - Accepted at
    with: group
  contexts:
    web:
      place: web::signed-in::start-group
- text: The Product opens the new group's page
  kind: product
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::group
---

# Start a top-level group

## Trigger

A person wants a new space for their organization to discuss and decide.

## Outcome

The group exists with its creator as its only admin, and the creator is on its page.

## Edge cases

- A trial group cannot be made Open.
- The handle must be unique; the form suggests one from the name.
