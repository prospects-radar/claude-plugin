---
name: daily-briefing
description: Start-of-day sales briefing from ProspectsRadar — new buying signals, tasks due, and the handful of prospects worth acting on today. Use when the user asks what to do today, what changed in their pipeline, for a morning briefing, or "anything new on my prospects?".
---

# Daily briefing

Give the user a short list of things to do today, ranked by how much each one is worth. They want decisions, not a data dump.

## Gather

Run these in parallel:

1. `pipeline_stats` for the overall picture and how many tasks are due.
2. `list_tasks` with `due_before` set to today's date, so overdue tasks show up too.
3. `get_buying_signals` with `days: 7` (use `days: 3` on a Monday-to-Monday rhythm if the user says so).

Then, for the prospects behind the strongest signals (highest `significance_score`, at most five), call `get_prospect` to get their score and buying readiness.

## Rank

A prospect moves up when it has:
- a fresh, significant signal (a new hire in the buying role, funding, expansion, a tender, a relevant job posting)
- a high score, or a buying readiness stage that is moving forward
- an interest state of `active` (the user already follows it)

A signal at a prospect scored below 40 is worth mentioning only when it is unusually strong.

## Write

Keep it under one screen:

1. **Today** — at most five actions, each with the company, the reason in one line (name the signal and its date), and the concrete next step.
2. **Due tasks** — open tasks due today or overdue, one line each.
3. **Pipeline in one line** — total prospects, how many are active, signals this week.

Close by offering to prepare a brief (`prospect-brief` skill) or to plan outreach (`plan-outreach` skill) for the top item. Never create tasks or change states during a briefing unless the user asks.
