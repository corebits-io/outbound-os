# Playbook 06 — Push to Instantly

**Goal:** Load the leads + personalization into an Instantly campaign, ready to send. **This stage requires explicit user approval before any data leaves the folder.**

## Pre-flight (do this first, every time)
1. Confirm `.env` has `INSTANTLY_API_KEY`.
2. Confirm only `validated` (or at worst `likely`) emails are included. **Exclude every `guess`.**
3. Open `reference/infrastructure.md` and check the **"Cleared to send?"** line. If it isn't `YES`, stop and tell the user the domains aren't warmed up yet — do not load a real campaign. If that file is empty/missing, the user hasn't run Playbook 00; ask them before going further.
4. **Compliance check:** the sequence has a real opt-out and honest sender info, and every claim is provable (see `playbooks/05`). Don't push copy that fails this.
5. Build the upload file: one row per lead with `email` + every `{{custom_field}}` the sequence uses (from `sequences/custom-fields.md`).

## Steps
1. **Read the live API docs** in `reference/apis.md` (Instantly section) and confirm current endpoints/fields — Instantly's API changes. Remember the Cloudflare **user-agent header**.
2. Authenticate with the Bearer key.
3. **Create or select the campaign** (ask the user which). Set the sequence copy + delays from `sequences/`. New campaigns are created as **Draft** — they send nothing until activated.
4. **Attach the RIGHT inboxes.** `GET /api/v2/accounts` and check each inbox's `warmup_status` + `status`. Attach the **specific warmed, active inboxes designated for THIS campaign** — a deliberate, sized set you confirm with the user — **not the whole fleet** (an account can hold dozens or hundreds of inboxes; attaching all of them is wrong and risky). If none are warmed, stop — same gate as `reference/infrastructure.md`. Never attach cold inboxes.
5. **Set campaign settings** (confirm with the user): a sane `daily_limit` (≈20–30 per inbox/day after warmup), `open_tracking`/`link_tracking` per preference, `stop_on_reply: true`, and the send schedule/timezone.
6. **Add leads** with their `custom_variables` (they become `{{merge}}` tags). Include only `validated`/`likely` emails — exclude every `guess`, undeliverable, or no-email lead.
7. **Dry run on 2–3 leads first**, show the user the rendered preview in Instantly, get approval, then load the rest.
8. Update `prospects/prospects.csv` status → `pushed`. Log counts in `reports/log.md`.

## Guardrails
- **Loading, configuring, and attaching inboxes never sends.** Only `POST /api/v2/campaigns/{id}/activate` starts sending — **never call it without the user's explicit "go."** Loading ≠ launching.
- Don't print full API keys in the chat or logs.
- If an upload partially fails, report exactly which leads didn't load and why; don't silently drop them.

**Checkpoint:** Report # loaded, # excluded (and why), campaign name. Then schedule the first performance pull (Playbook 07).
