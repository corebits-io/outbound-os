---
name: Push to Sequencer
description: Load the campaign + personalized leads into Instantly or Smartlead as a DRAFT — create the campaign, attach warmed inboxes, set limits, map custom fields. It never sends. Use after preview-qa is approved.
allowed-tools: Read Write Edit Bash WebFetch
---

# Push to sequencer

Load everything into the sender, ready to launch — but in DRAFT.

**Read:** `sequences/sequence-*.md`, `sequences/leads-upload.csv`, `sequences/custom-fields.md`, `reference/infrastructure.md`.
**Target:** Instantly or Smartlead (whichever key is in `.env`). Endpoints in `reference/apis.md`.

## Steps (full detail in `playbooks/06-push-to-instantly.md`)
1. Pre-flight: only `validated`/`likely` emails; check `infrastructure.md` → "Cleared to send?"; compliance.
2. Create the campaign + set the sequence/delays. (Instantly is behind Cloudflare — send a normal `User-Agent` header.)
3. Attach the RIGHT warmed inboxes — a deliberate set you confirm, NOT the whole fleet; set a sane daily limit + stop-on-reply.
4. Add leads with custom variables mapped. Dry-run 2–3, show the user, then load the rest. Set status `pushed`.

**Rule (hard gate):** loading ≠ launching. NEVER activate / start sending without the user's explicit "go."
