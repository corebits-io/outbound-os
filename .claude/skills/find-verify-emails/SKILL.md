---
name: Find & Verify Emails
description: Find a valid email (and phone if needed) for each chosen person, spending as few credits as possible — free/public first, then the paid enrichment waterfall, then verify. Use after research, before writing or pushing.
allowed-tools: Read Write Edit Bash WebFetch
---

# Find & verify emails

Get a deliverable email per prospect, cheaply, and tag confidence honestly.

**Read:** the active campaign's `prospects/prospects.csv`.
**Write:** `prospects.csv` with `email, email_confidence (verified|likely|guess), phone, phone_source, enrichment_source`; advance status `enriched` → `validated`.

## Steps (full detail in `playbooks/04-enrich-and-validate.md`; endpoints in `reference/apis.md`)
1. Free / self-found first (team pages, public profiles, verifiable patterns).
2. Paid waterfall only for gaps: BetterContact → Findymail → Prospeo — stop at the first valid hit.
3. Validate before use. Map status → confidence (`deliverable` = verified, `catch_all_safe` = likely, `undeliverable` = exclude).

**Rule:** never send a `guess`. Log credits per tool in `reports/log.md`.
