---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The Visitor follows the invitation link from their email
  kind: actor
  capability: accept-group-invitation
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::group
- text: The Visitor enters the code emailed to the invited address
  kind: actor
  capability: sign-in
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product signs the Visitor in
  kind: product
  capability: sign-in
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product accepts the invitation and shows the group
  kind: product
  capability: accept-group-invitation
  actor: user
  entities:
  - entity: membership
    effect: changes
    from: Invited
    to: Active
    facts:
    - Accepted at
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
- text: The User opens the group's threads
  kind: actor
  capability: view-group
  actor: user
  entities:
  - entity: thread
    effect: reads
    facts: []
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::group
---

# Follow an invitation and sign in

## Trigger

An invitee opens their invitation email without being signed in.

## Outcome

The person is an active member and sees the group.
