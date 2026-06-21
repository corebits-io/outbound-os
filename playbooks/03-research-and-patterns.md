# Playbook 03 — Research & Find Patterns

**Goal:** Understand each account and the list as a whole, so copy is built on real problems and signals — the "Claygent" research step, done in-house.

## Inputs
- `accounts/accounts.csv`, `prospects/prospects.csv`, all three brain files.

## Per-account research (save to `research/<domain>.md`)
For each account, gather what's publicly available and relevant to the offer:
- What the company does, who they serve, how they make money.
- **Intent / timing signals:** hiring (which roles), recent funding, new product or market, leadership changes, press, expansion, tech stack changes, public complaints or reviews.
- A specific, true observation we could reference in an email ("noticed you're hiring 4 SDRs" / "saw you just launched X").
- The **problem hypothesis:** what pain do they likely have that our offer solves, based on evidence.

Keep each note tight: 5–8 bullets. Cite source URLs. Mark anything uncertain as `likely` or `guess`.

## Cross-account pattern pass (save to `research/_patterns.md`)
After researching the batch, step back and find patterns across the list:
- Recurring problems or triggers (e.g., "most are hiring sales but have no enrichment stack").
- Shared language they use about their pain.
- Segments worth splitting into different angles/sequences.

These patterns drive smarter, segment-level copy in Playbook 05.

## Recording results
- For each researched person, set `status` → `researched` in `prospects/prospects.csv` (column list is in `CLAUDE.md` → "Data formats").
- A research note exists at `research/<domain>.md` for every account you advanced; the cross-account view lives in `research/_patterns.md`.

**Done when:** every prospect you're carrying forward is at `status = researched` and has a research note. Accounts you decided to drop are marked, not silently deleted.

## Guardrails
- Only record verifiable facts. No invented "I saw your post" if you didn't.
- Don't over-research low-score accounts; spend effort proportional to fit.

**Checkpoint:** Summarize the top 3 patterns found and proposed segments. Then move to Playbook 04.
