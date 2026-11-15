---
name: prospect-brief
description: One-page brief on a single ProspectsRadar prospect before a call, meeting or first outreach — why it fits, what changed recently, who sits on the buying committee, and a suggested opening. Use when the user names a company and asks to prep, research, brief, or "tell me about" it, or asks why a prospect scores the way it does.
---

# Prospect brief

## Find the prospect

If the user gives a name rather than an id, call `search_prospects` with `query` set to the name. Prospects are scored per product: when the company shows up under more than one product, ask which product the conversation is about, or brief the highest-scoring one and say so.

## Gather

Run in parallel once you have the prospect id:

- `get_prospect` — score, the score breakdown, buying readiness, company basics
- `list_stakeholders` — the buying committee (DMU)
- `get_buying_signals` with the `prospect_id` and `days: 90`
- `list_tasks` with the `prospect_id` — what is already planned

Then call `get_company_news` with the company id for the last 90 days if the signals leave gaps.

## Write the brief

1. **Fit** — the overall score and what drives it, in plain words. Use the score breakdown; if the prospect is not qualified, give the rejection reason.
2. **Timing** — buying readiness stage and the two or three signals that matter most, each with its date. Say plainly when nothing recent happened.
3. **Buying committee** — decision makers first, then influencers. Name, role, department, and LinkedIn when present. Mention confidence when it is low.
4. **Open tasks** — what is already planned.
5. **Opening angle** — one or two sentences that link a recent signal to the problem the product solves. This is a suggestion for the user, not a message to send.

Every fact comes from a tool result. Do not invent people, titles, events or numbers; if ProspectsRadar has no data for a section, say so in that section.
