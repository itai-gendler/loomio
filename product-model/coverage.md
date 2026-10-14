---
scope: Groups, membership and permissions, discussions, comments, polls, votes and outcomes in the Rails application and Vue client.
method: Static inspection of source, configuration and the English user manual; no code was run.
covered:
- description: Authorization rules
  paths:
  - app/models/ability/
- description: Services for groups, memberships, threads, discussions, comments, polls, votes, outcomes, templates, tags, reactions, bookmarks, tasks, follows, translation, search, reports and exports
  paths:
  - app/services/group_service.rb
  - app/services/group_service/
  - app/services/membership_service.rb
  - app/services/membership_request_service.rb
  - app/services/discussion_service.rb
  - app/services/topic_service.rb
  - app/services/topic_item_service.rb
  - app/services/comment_service.rb
  - app/services/poll_service.rb
  - app/services/stance_service.rb
  - app/services/anonymous_ballot_service.rb
  - app/services/outcome_service.rb
  - app/services/stv_count_service.rb
  - app/services/stv_count_service/
  - app/services/poll_markdown_results_service.rb
  - app/services/thread_markdown_service.rb
  - app/services/poll_template_service.rb
  - app/services/discussion_template_service.rb
  - app/services/tag_service.rb
  - app/services/reaction_service.rb
  - app/services/bookmark_service.rb
  - app/services/task_service.rb
  - app/services/group_follow_service.rb
  - app/services/translation_service.rb
  - app/services/search_service.rb
  - app/services/participation_report_service.rb
  - app/services/report_service.rb
  - app/services/group_export_service.rb
  - app/services/digest_service.rb
  - app/extras/user_inviter.rb
- description: 'Account services: registration, sign-in codes, profile, deactivation and merging'
  paths:
  - app/services/registration_service.rb
  - app/services/login_token_service.rb
  - app/services/user_service.rb
  - app/services/merge_users_service.rb
  - app/workers/deactivate_user_worker.rb
  - app/workers/redact_user_worker.rb
- description: Inbound email routing
  paths:
  - app/mailboxes/
  - app/services/received_email_service.rb
- description: Notification creation and recipient routing
  paths:
  - app/services/notification_service.rb
  - app/services/notification_delivery_routers/
  - app/services/notification_audience_service.rb
- description: Records and validations
  paths:
  - app/models/
- description: Web API controllers
  paths:
  - app/controllers/api/v1/
- description: User API controllers
  paths:
  - app/controllers/api/b2/
- description: Page controllers and sign-in handoffs
  paths:
  - app/controllers/memberships_controller.rb
  - app/controllers/merge_users_controller.rb
  - app/controllers/login_tokens_controller.rb
  - app/controllers/identities/
  - app/helpers/pending_actions_helper.rb
- description: Poll type definitions
  paths:
  - config/poll_types.yml
- description: Jobs that close polls, remind about tasks, move items and remove deleted groups
  paths:
  - app/workers/close_expired_poll_worker.rb
  - app/workers/destroy_group_worker.rb
  - app/workers/move_comments_worker.rb
- description: Web client
  paths:
  - vue/src/
exclusions:
- description: Development scenarios, tests and fixtures
  paths:
  - app/controllers/dev/
  - app/helpers/dev/
  - test/
  - spec/
  - vue/tests/
- description: User manual content and its site builder
  paths:
  - docs/
- description: Email and page templates, which hold wording and layout
  paths:
  - app/mailers/
  - app/views/
- description: Deployment, mail relay, push relay and collaborative-editing infrastructure
  paths:
  - deploy/
  - haraka/
  - push-relay/
  - hocuspocus/
  - Dockerfile
  - bin/
  - script/
- description: Database migrations and schema
  paths:
  - db/
- description: Static assets, fonts and themes
  paths:
  - public/
unmapped:
- description: 'Chat integrations and webhooks: deliveries to chat systems Loomio does not own'
  paths:
  - app/services/chatbot_service.rb
  - config/webhook_event_kinds.yml
- description: 'Server API: operator account administration for self-hosted servers'
  paths:
  - app/controllers/api/b3/
- description: 'Instance administration area: internal operator tooling'
  paths:
  - app/controllers/admin/
- description: 'Demo groups, trials, billing and the subscription portal: commercial plumbing around the product'
  paths:
  - app/services/demo_service.rb
  - app/services/demo_group_template_service.rb
  - app/services/subscriptions/
  - app/controllers/subscription_portal_controller.rb
- description: 'iOS companion and mobile sessions: a native shell around the same web app'
  paths:
  - ios/
  - app/services/mobile/
  - app/controllers/mobile/
- description: 'Web push delivery: a delivery channel for notifications already modelled as Product steps'
  paths:
  - app/services/web_push_service.rb
  - app/services/push_subscription_service.rb
- description: 'Passkey and password management: credential upkeep beside sign-in'
  paths:
  - app/services/passkey_service.rb
- description: 'Template ordering and template file import and export: list arrangement and file sharing'
  paths:
  - app/services/template_file_service.rb
- description: 'Contact form: a message to the server''s operators'
  paths:
  - app/services/contact_message_service.rb
- description: 'Maintenance jobs: repairs, cleanup and caches'
  paths:
  - app/services/cleanup_service.rb
  - app/services/record_count_repair_service.rb
  - app/services/inline_image_attachment_repair_service.rb
limitations: []
---

# Coverage
