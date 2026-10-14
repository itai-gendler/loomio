---
appliesTo:
- type: entity
  id: group
  effect: removes
permits:
- unattended: true
  when:
  - entity: server-settings
    fact: Automatic cleanup
    is: Enabled
references:
- kind: code
  role: implementation
  target: app/workers/destroy_group_worker.rb
- kind: code
  role: implementation
  target: app/services/cleanup_service.rb
---

# Only the server removes a deleted group, once the grace period has passed

Nobody removes a group permanently by hand. Where automatic cleanup is enabled, the server removes a group the grace period after it was deleted; a group restored and deleted again starts a new grace period.
