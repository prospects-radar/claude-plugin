---
name: pipeline-review
description: Review the health of a ProspectsRadar pipeline — score distribution, which high scorers nobody follows yet, which followed prospects went quiet, and what to clean up. Use for a weekly pipeline review, "how is my pipeline doing", "which prospects should I focus on", or "clean up my prospect list".
---

# Pipeline review

## Gather

1. `list_products` — if there is more than one product, review per product, because scores from different products are not comparable.
2. `pipeline_stats` — totals, interest states, score distribution, task load.
3. Per product, `search_prospects` with:
   - `min_score: 70`, `interest_state: "neutral"`, `limit: 25` → strong prospects nobody follows yet
   - `interest_state: "active"`, `limit: 25` → what the user follows now
4. `get_buying_signals` with `days: 30` and a high `limit` to see which followed prospects have recent activity.
5. `list_tasks` for the open task load.

## Analyse

Report on four things:

- **Untapped** — neutral prospects with a high score and a recent signal. These are the best candidates to follow.
- **Gone quiet** — active prospects without signals in 30 days and without open tasks.
- **Overload** — more active prospects than the user can work, or lots of overdue tasks.
- **Shape** — whether the score distribution suggests the ICP is too broad (many low scores) or too narrow (very few prospects). If so, point to the `tune-icp` skill.

## Act only with consent

Propose changes as a list (follow these, set these to `off`) and ask before changing anything. Then call `update_prospect_state` with the default `dry_run: true` first, show the preview, and commit with `dry_run: false` only after the user confirms.
