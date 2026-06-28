---
name: Source Accounts
description: Find and qualify target companies for the current campaign's ICP. Use at the start of a campaign or to scale the list. Pulls from Apify (e.g. the YC directory) when APIFY_API_TOKEN is set, otherwise free web search + public directories.
allowed-tools: Read Write Edit Bash WebSearch WebFetch Glob
---

# Source accounts

Build a qualified list of companies that match the campaign's ICP.

**Read:** the active campaign's `01-offer-and-icp.md` and `04-fit-examples.md`.
**Write:** `campaigns/<campaign>/accounts/accounts.csv` (columns in `CLAUDE.md` → Data formats), status `qualified`.

## Steps (full detail in `playbooks/01-source-accounts.md`)
1. Learn the pattern from the ICP + good/bad fit examples.
2. Source candidates: if `APIFY_API_TOKEN` is set, use an Apify actor (e.g. the YC directory scraper — see `reference/apis.md` → Apify); otherwise free web search + public directories. De-dupe by domain.
3. Qualify each: `why_fit`, `fit_score` (1–5), `signal`, `source_url`. Drop obvious bad fits.
4. Work in batches (~25), show the user, get a thumbs-up before continuing.

**Rule:** quality over volume. Never fabricate a company or a signal — if you can't verify a fit, lower the score.
