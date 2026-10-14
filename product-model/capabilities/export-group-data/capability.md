---
domain: group-settings
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/services/group_export_service.rb
- kind: code
  role: implementation
  target: app/services/group_service.rb#export
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/data_export/index.md
---

# Export group data

Download a group's data as CSV for spreadsheets, HTML for archiving, or JSON for moving to another Loomio server. Files are prepared in the background and emailed as a link that lasts a week.
