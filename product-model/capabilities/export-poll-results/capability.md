---
domain: polls
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: app/models/ability/poll.rb
- kind: code
  role: implementation
  target: vue/src/shared/services/poll_service.js
---

# Export poll results

Download a poll's results to open in a spreadsheet, or an STV Election's ballots as a BLT file, once results are available.
