---
name: Pick the Person
description: Choose the single best contact per account — the person who owns the problem, not just the CEO. Use after accounts are qualified, before research and enrichment.
allowed-tools: Read Write Edit WebSearch WebFetch
---

# Pick the person

For each account, pick the right human to contact and say why.

**Read:** the active campaign's `accounts/accounts.csv`, `02-personas.md`.
**Write:** `campaigns/<campaign>/prospects/prospects.csv` (schema in `CLAUDE.md`), status `person_picked`. Leave `email`/`phone` blank (enrichment fills them).

## Steps (full detail in `playbooks/02-pick-the-person.md`)
1. Weigh who owns the problem vs. decision power vs. company size — don't default to the CEO. (For a founder-to-founder offer, the founder IS the right contact.)
2. Capture `first_name, last_name, title, linkedin_url`, and a mandatory `why_this_person`.
3. Flag accounts with no clear fit instead of forcing a bad pick.

**Rule:** `why_this_person` is mandatory — it's how the user trusts your judgment.
