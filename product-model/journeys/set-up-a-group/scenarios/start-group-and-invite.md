---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters a name, handle, description and privacy for the new group
  kind: actor
  capability: start-group
  actor: user
  entities:
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::start-group
- text: The Product creates the group and makes the User its first admin
  kind: product
  capability: start-group
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
    as: creator
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
  capability: start-group
  actor: user
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::group
- text: The User enters email addresses of the first people to invite
  kind: actor
  capability: invite-to-group
  actor: user
  entities: []
  contexts:
    web:
      place: web::signed-in::group
- text: The Product invites each person and emails them a single-use invitation link
  kind: product
  capability: invite-to-group
  actor: user
  entities:
  - entity: membership
    as: invitation
    effect: creates
    to: Invited
    facts:
    - Role
    - Delegate
    - Vote weight
    - Invited by
  contexts:
    web:
      place: web::signed-in::group
---

# Start a group and invite people

## Trigger

A person wants a new space for their organization and the people in it.

## Outcome

The group exists with its creator as admin and the first invitations are sent.
