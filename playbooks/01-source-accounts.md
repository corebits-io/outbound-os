# Playbook 01 — Source Accounts

**Goal:** Build a list of companies that match the ICP, qualify them, and save to `accounts/accounts.csv`.

## Inputs to read first
- `01-offer-and-icp.md`, `04-fit-examples.md` (especially the "pattern" section).

## Steps
1. **Learn the pattern.** From the good-fit / bad-fit examples, write the explicit traits and disqualifiers into `04-fit-examples.md` under "The pattern." Confirm it with the user before sourcing at scale.
2. **Source candidates.** Use the available sourcing methods, in this priority order:
   - Built-in web search for industry directories, lists, "best X companies", local association member lists, job boards (a company hiring for role Y is a buying signal), review sites, etc.
   - Any connected data MCP/tool the user has (e.g., Apollo, Apify scrapers, a prospecting connector). Check what's available before assuming you must scrape manually.
   - The user's own seed lists if provided.
3. **Qualify each candidate** against the pattern. For every company record: `why_fit`, a `fit_score` 1–5, the `signal` that makes now a good time, and the `source_url`.
4. **Drop the obvious bad fits** (exclusions in `01-offer-and-icp.md`). Note borderline ones as score 2 rather than deleting, so the user can review.
5. **Work in batches of ~25.** Show the user the batch, get a thumbs up on quality, then continue. This calibrates you early and avoids wasting a run on the wrong direction.

## Output
`accounts/accounts.csv` with columns from `CLAUDE.md`. Status = `qualified`.

## Guardrails
- Don't fabricate companies or signals. If you can't verify a fit reason, lower the score.
- De-duplicate by domain.
- Aim for fit, not count. Tell the user honestly if the niche is thin and the list is short.

**Checkpoint:** Summarize: # sourced, # qualified (score ≥3), top signals seen. Then move to Playbook 02.
