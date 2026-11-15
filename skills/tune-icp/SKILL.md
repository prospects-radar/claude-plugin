---
name: tune-icp
description: Inspect and improve the ideal customer profiles (ICPs) and product definitions that drive ProspectsRadar discovery and scoring. Use when the user asks why they get too few, too many, or the wrong prospects, wants to change target industries, regions, or company size, or wants a profile review.
---

# Tune the ICP

## Understand the current setup

1. `list_products` — the products and their ICPs.
2. `pipeline_stats` and, per product, `search_prospects` with `limit: 25` — what the current profile actually produces. Look at the industries, sizes and cities of the top results and at how many prospects score low.

## Diagnose

Name the problem before proposing a fix:

- **Too few prospects** — industries, regions or size bands too narrow, or a Dutch province limit.
- **Too many low scores** — the ICP is broader than the product description; industries or size bands let in companies that cannot buy.
- **Wrong kind of company** — the description, niche qualifier or business characteristics do not describe the observable traits of a buyer.

## Change it

- Look up codes with `search_industry_codes` (in the classification the ICP uses: sbi, nace or naics) and regions with `search_regions`. Never guess codes or region ids.
- `update_icp` replaces list fields (industry codes, regions, technologies, business characteristics). Send the full new list, not just the additions.
- Always call `update_icp` (or `create_icp`, `update_product`) with the default `dry_run: true` first, show the before and after, and commit with `dry_run: false` only after the user confirms.

## Profile review (costs tokens)

`review_profile` runs ProspectsRadar's own AI review of a product profile and charges account tokens. Call it with `dry_run: true` to get the cost, tell the user the number, and run it with `dry_run: false` only when they agree.

Changes to an ICP affect future discovery and scoring for the whole account. Say so when committing.
