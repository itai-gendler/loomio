---
appliesTo:
- type: entity
  id: membership
  facts:
  - Accepted at
- type: capability
  id: invite-to-group
- type: capability
  id: accept-group-invitation
references:
- kind: code
  role: implementation
  target: app/helpers/pending_actions_helper.rb#accept_pending_membership
- kind: code
  role: implementation
  target: app/models/topic.rb#members
- kind: code
  role: implementation
  target: app/services/membership_service.rb#redeem
---

# An invited person counts as a member before accepting

From the moment of the invitation the person is among the group's members: they hold votes in its polls open to everyone, receive its notifications, and can be made an admin or given a title. Accepting records when they joined and accepts their other pending invitations in the organization.
