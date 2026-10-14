---
availability:
- place: web::signed-in
- place: api
references:
- kind: code
  role: implementation
  target: app/services/participation_report_service.rb
- kind: code
  role: implementation
  target: app/controllers/api/v1/reports_controller.rb
- kind: code
  role: implementation
  target: app/controllers/api/b2/reports_controller.rb
- kind: doc
  role: intent
  target: docs/en/user_manual/groups/participation_report/index.md
---

# View participation report

See how much people took part in chosen groups over a period: actions per month, tag usage, actions and voting record per person, and activity by country. People see results only for groups they belong to.
