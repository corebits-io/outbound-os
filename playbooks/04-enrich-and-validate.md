# Playbook 04 — Enrich & Validate (save credits)

**Goal:** Get a valid email (and phone if needed) for each chosen person, spending as few paid credits as possible.

## The credit-saving order (do NOT skip to paid first)
1. **Free / self-found first.** Try to find or infer the contact from public sources: company team/contact pages, public profiles, patterns you can verify (e.g., a published `first@domain.com` format on the site). Only treat self-found emails as `likely` unless validated.
2. **Paid APIs only for the gaps.** For people you still couldn't get, call the enrichment APIs in a **waterfall** — stop as soon as one returns a hit so you don't pay twice:
   - **BetterContact** first — it's itself a waterfall across 20+ sources and you only pay for valid data. Good default.
   - **Findymail** and **Prospeo** as additional/fallback finders (name + domain, or LinkedIn URL → email/mobile).
   - Mobile/phone: use **Prospeo Mobile Finder** or BetterContact's phone result only when the campaign actually uses phone.
   See exact endpoints and auth in `reference/apis.md` — re-read the live docs before coding, they change.
3. **Validate before sending.** Run every email through validation (BetterContact/Findymail return validity; or a dedicated validator). Drop or downgrade anything that isn't deliverable. Catching bounces here protects your domain reputation.

## Recording results
Update `prospects/prospects.csv` with `email`, `email_confidence`, `phone`, `phone_source`, `enrichment_source` (which tool found it), and advance `status` in two steps:
- **`enriched`** — set this the moment you've found and recorded an email (from any source), before validation.
- **`validated`** — set this only after that email passes the validation step below. Confidence then becomes `verified` (validated deliverable). Leave it `likely` (found, not validated) or `guess` (pattern only) if it didn't pass.

So the flow per person is: find email → `enriched` → validate → `validated` + `verified`. Anything stuck at `guess` is excluded from the send.

**Done when:** every carried-forward prospect is either at `status = validated` with a `verified`/`likely` email, or flagged `no_email` and excluded.

## Guardrails
- **Never blast a `guess` email.** Either validate it or exclude it.
- Log how many credits each tool consumed in `reports/log.md` so the user sees cost per campaign.
- Batch API calls; handle the async pattern for BetterContact (submit request → poll for results).

**Checkpoint:** Report find rate (% with a usable email), validation rate, and credits spent per tool. Then move to Playbook 05.
