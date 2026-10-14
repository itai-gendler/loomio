---
appliesTo:
- type: entity
  id: subscription
  facts:
  - Member limit
  - Thread limit
- type: capability
  id: invite-to-group
- type: capability
  id: start-discussion
references:
- kind: code
  role: implementation
  target: app/extras/user_inviter.rb#authorize_add_members!
- kind: code
  role: implementation
  target: app/models/topic.rb#enforce_subscription_thread_limit!
---

# An organization stays within its plan's member and thread limits

Where a plan sets a member limit, invitations that would take the organization's distinct members past it are refused; where it sets a thread limit, no thread is started once the organization holds that many.
