# Playbook 02 — Pick the Right Person

**Goal:** For each qualified account, choose the single best person to contact and record *why*. Save to `prospects/prospects.csv`.

## Inputs
- `accounts/accounts.csv`, `02-personas.md`.

## How to choose (don't default to the CEO)
For each account, weigh:
1. **Who owns the problem** our offer solves day-to-day? That person feels the pain and replies.
2. **Company size.** At a 10-person company the founder may own everything; at a 500-person company you want the function lead, not the C-suite.
3. **Decision power vs. pain.** Sometimes the best entry is the person in pain (champion) who escalates internally, not the economic buyer. Use the picking rules in `02-personas.md`.
4. **Signals.** Recent role changes, a relevant post, ownership of a named initiative, who's quoted on the topic. These beat title alone.

## Steps
1. For each account, identify 1 primary contact (optionally 1 backup) matching a persona.
2. Capture: `first_name, last_name, title, linkedin_url`, and a one-line `why_this_person`.
3. Leave `email` / `phone` blank for now — that's the enrichment stage.
4. Flag any account where no clear person fits, rather than forcing a bad pick.

## Output
`prospects/prospects.csv`, status = `person_picked`. The `why_this_person` column is mandatory — it's how the user trusts your judgment.

**Checkpoint:** Show 5–10 example picks with reasoning for the user to sanity-check, then continue across the list. Move to Playbook 03.
