# Running Outbound OS as a service (for clients)

The same folder is your repeatable delivery engine. Each client is just another campaign.

## One client = one campaign folder
- Copy `campaigns/_TEMPLATE` to `campaigns/<client-name>/` and fill in their brain (the onboarding prompt does this).
- The skills, playbooks, and wiring stay identical — only the brain changes. That's the leverage.

## Keep client data private
- Real client campaigns are **gitignored** by default (`.gitignore` ships only `_TEMPLATE` + `_EXAMPLE` + the public demo). Never push a client's prospects to a public repo.
- Use **separate sending infrastructure per client** (their domains/inboxes), recorded in their own setup.
- Each client should use **their own** API keys/credits where possible.

## A clean delivery rhythm
1. **Onboard** — fill the brain from a short kickoff (offer, ICP, personas, winning emails).
2. **Build** — source → qualify → research → enrich → write → preview → push (draft).
3. **Approve & launch** — client signs off on the preview; you launch.
4. **Improve** — run `/improve-loop` every few days; report reply rate + the one change you're testing. This is what earns retention.

## Pricing shape (rough, adjust to you)
- A setup/build fee + a monthly run-and-improve retainer is the common shape. Price on outcomes (meetings/replies), not "emails sent."

## Where it's headed (roadmap)
- Multi-channel (LinkedIn via HeyReach, calling), a LinkedIn/Reddit intent layer, and scheduled auto-improve — all addable via the adapter pattern without changing the core.
