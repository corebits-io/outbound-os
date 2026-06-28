# System overview — how Outbound OS fits together

One folder that runs a whole outbound motion inside Claude Code. The pieces:

- **The brain** (`campaigns/<name>/01–04` + `winning-emails.md`) — you describe the offer, ICP, personas, value prop, fit examples, and your best emails. Everything else is generated from this.
- **The skills** (`.claude/skills/`) — 12 invokable actions (`/source-accounts`, `/pick-person`, …). Type `/` to see them. They're the entry points.
- **The playbooks** (`playbooks/00–07`) — the detailed step-by-step each skill follows. Skills stay short; playbooks hold the depth.
- **The reference** (`reference/`) — technical notes: API endpoints (`apis.md`), install (`getting-started.md`), sending setup (`infrastructure.md`), the pipeline diagram (`workflow.md`).
- **This knowledge-base** (`knowledge-base/`) — the "why/how" context: deliverability, a glossary, swipe files, and running it as a service.
- **The campaigns** (`campaigns/`) — the working data: accounts, prospects, research, sequences, reports. One folder per offer/client.
- **The senders** — Instantly or Smartlead (push), plus Apify (sourcing) and BetterContact/Findymail/Prospeo (enrichment).

## The 4-tool stack
Claude Code (the brain) · **Apify** (sourcing) · **BetterContact** (find + verify emails) · **Instantly / Smartlead** (the sequencer).

## The flow (and the status it sets)
`source-accounts` (qualified) → `qualify-icp` → `find-signals` → `pick-person` (person_picked) → `research-account` (researched) → `find-verify-emails` (enriched → validated) → `write-copy` → `build-sequence` (written) → `preview-qa` → `push-to-sequencer` (pushed, **draft**) → `improve-loop`.

## The two rules that never bend
1. **Never invent data** — tag every email `verified` / `likely` / `guess`; never send a guess.
2. **Loading ≠ launching** — the system can build and load a campaign, but **never sends without your explicit "go."**

## Autonomy
Autopilot *within* a stage; checkpoint *between* stages; hard stop before anything irreversible (sending, large paid batches). See `CLAUDE.md` → "Autonomy & control."
