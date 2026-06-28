---
name: Qualify ICP (Scorer)
description: Score and filter sourced accounts against the campaign's ICP and fit-examples, dropping bad fits. Use after sourcing, or to re-score a list before research and enrichment.
allowed-tools: Read Write Edit WebSearch WebFetch
---

# Qualify ICP

Score each account in `accounts.csv` against the campaign's ICP so only real fits move forward.

**Read:** the active campaign's `accounts/accounts.csv`, `01-offer-and-icp.md`, `04-fit-examples.md`.
**Write:** updated `accounts.csv` — a `fit_score` (1–5) + sharpened `why_fit`; mark exclusions `do_not_contact`.

## Rubric
- 5 = exact ICP match + a live signal · 4 = fits core criteria · 3 = fits, weaker signal · 2 = borderline (keep for review) · 1 = weak / likely drop.
- Apply the hard exclusions from `01-offer-and-icp.md` (competitors, existing clients, wrong geo/size) → `do_not_contact`.
- **Selective targeting:** prefer accounts where the offer clearly lands (for the founder demo offer: products with a real, engaged audience worth reaching). Note why in `why_fit`.

**Rule:** don't pad the list to hit a number. Say so honestly if the niche is thin.
