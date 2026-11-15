---
name: plan-outreach
description: Plan multi-threaded outreach to one ProspectsRadar prospect — pick the stakeholders, choose a channel per person, draft the messages, and create the tasks in ProspectsRadar. Use when the user wants to reach out to, approach, contact, or follow up with a prospect or its buying committee.
---

# Plan outreach

## Gather

Use the same calls as the `prospect-brief` skill: `get_prospect`, `list_stakeholders`, `get_buying_signals` (`days: 90`) and `list_tasks` for the prospect. Do not plan contact with someone who already has an open task.

## Plan

Pick two or three stakeholders: the decision maker plus one or two influencers. For each, choose a channel based on what is available:

- `email_outreach` when there is an email address
- `linkedin_connect`, then `linkedin_message`, when there is a LinkedIn URL and no email
- `phone_outreach` only when the user says they call

Draft a short message per person in the user's language. Anchor it on a real signal with its date and on the person's role. No more than 90 words, no invented facts, no claims about the user's product beyond what the user or the product description says.

## Create the tasks

Show the plan and the drafts, then ask whether to create the tasks. On yes:

1. Call `create_task` per stakeholder with `prospect_id`, `action_type`, `stakeholder_id` and the default `dry_run: true`.
2. Show the previews.
3. Commit each one with `dry_run: false` after the user confirms.

If the prospect is not followed yet, offer to set it to `active` with `update_prospect_state` (preview first, then commit).

The plugin never sends email or LinkedIn messages itself. Tasks land in ProspectsRadar, where the user sends them.
