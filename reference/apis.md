# API Reference

> **Rule for the operator:** APIs change. Before writing or running integration code, fetch the live docs linked below and confirm the current endpoint paths, field names, and auth. The notes here are a starting map, not gospel.

All keys live in `.env`. Never print full keys. Use the env var names shown.

---

## Apify (sourcing at scale) — `APIFY_API_TOKEN`
- **Docs:** https://docs.apify.com/api/v2 · Token: https://console.apify.com/account/integrations
- **What we use it for:** pulling target companies at scale when free web search isn't enough — e.g., the **Y Combinator directory** (companies + founders + jobs), Google Maps lists, etc. `source-accounts` uses Apify when this token is set, else free web search + public directories.
- **Run an actor + get results in one call:** `POST https://api.apify.com/v2/acts/<actor-id>/run-sync-get-dataset-items?token=<APIFY_API_TOKEN>` with the actor's input JSON in the body → returns the dataset items directly.
- **YC sourcing:** use a YC directory actor (e.g., `clearpath/ycombinator-api-scraper`) filtered to batch / industry / region. **Free alternative:** YC's public **Algolia** index behind ycombinator.com/companies (same data the site's filters use) — no token needed.
- **Note:** most actors are pay-per-result (~$3.50/1k on common YC actors). Confirm the current actor id + input schema on its Apify page before running.

---

## Instantly (email sequencing) — `INSTANTLY_API_KEY`
- **Docs:** https://developer.instantly.ai/ (API v2) · machine index: https://developer.instantly.ai/llms.txt
- **Base URL:** `https://api.instantly.ai`  ·  **Auth:** `Authorization: Bearer <INSTANTLY_API_KEY>` header.
- **Gotcha (verified 2026-06):** Instantly is behind Cloudflare, which **blocks default/blank user-agents (403 / "error code: 1010")**. Send a normal browser `User-Agent` header on every request.

**Create a campaign — lands in Draft (status 0 = NOT sending):** `POST /api/v2/campaigns`
- Required: `name`, `campaign_schedule`. It does **not** send until you call activate (below).
- `campaign_schedule`: `{ "schedules":[ { "name","timing":{"from":"09:00","to":"17:00"}, "days":{"0":false,"1":true,...,"6":false}, "timezone" } ] }`. **Timezone must be from Instantly's enum** — `America/Detroit` verified working; `America/New_York` was rejected, so use a known-good value.
- `sequences`: `[ { "steps":[ { "type":"email","delay":<days>,"delay_unit":"days","variants":[ {"subject","body"} ] } ] } ]`. Only the first sequence element is used; `body` is HTML; follow-up steps with `subject:""` thread under email 1.

**Add a lead (with personalization):** `POST /api/v2/leads`
- `{ "campaign":"<campaign_id>", "email","first_name","last_name","company_name", "custom_variables":{...} }` (only `email` required when `campaign` is set).
- **Custom variables land in the lead's `payload` and render as `{{merge}}` tags** (`custom_variables.hook` → `{{hook}}`). Variable names: letters/numbers/underscore only.

**Sending inboxes:** `GET /api/v2/accounts` → each has `email`, `warmup_status` (1 = warmup on), `status` (1 = active). **Attach only warmed, active inboxes** by setting the campaign's `email_list` to those emails (on create, or `PATCH /api/v2/campaigns/{id}`). Never attach cold inboxes.
- **Settings you can set/update:** `daily_limit`, `open_tracking`, `link_tracking`, `stop_on_reply`, `stop_on_auto_reply`, `insert_unsubscribe_header`, the schedule.

**Activate — THE send trigger (gate behind explicit approval):** `POST /api/v2/campaigns/{id}/activate`. Creating, loading, configuring, and attaching inboxes are all safe and send nothing. **Only activate sends — never call it without the user's explicit "go."**

**Analytics (the improve loop):** `GET /api/v2/campaigns/analytics?ids=<campaign_id>` → `leads_count, contacted_count, emails_sent_count, open_count, reply_count, link_click_count, bounced_count, unsubscribed_count` (per-step/variant breakdowns available too).

---

## Smartlead (email sequencing — alternative to Instantly) — `SMARTLEAD_API_KEY`
- **Docs:** https://api.smartlead.ai/ · Full reference: https://helpcenter.smartlead.ai/en/articles/125-full-api-documentation
- **Base URL:** `https://server.smartlead.ai/api/v1` · **Auth:** append `?api_key=<SMARTLEAD_API_KEY>` to every request (query param, not a header).
- **Create campaign:** `POST /api/v1/campaigns/create` with `{ "name": "..." }` → returns the `campaign_id`.
- **Set the sequence:** `POST /api/v1/campaigns/{campaign_id}/sequences` with the email steps + delays.
- **Add leads (with personalization):** `POST /api/v1/campaigns/{campaign_id}/leads` — array of `{ email, first_name, last_name, company_name, custom_fields:{...} }`, **max 100 per request** (paginate beyond that). Custom fields render as merge tags in the sequence.
- **Attach inboxes + schedule, then start.** **Same gate as Instantly: loading ≠ launching — never start sending without explicit approval.**
- Re-read the live docs for the current analytics endpoint (for the improve loop).

---

## BetterContact (waterfall enrichment) — `BETTERCONTACT_API_KEY`
- **Docs:** https://doc.bettercontact.rocks/api-reference/  ·  machine index: https://doc.bettercontact.rocks/llms.txt
- **Auth:** `X-API-Key: <BETTERCONTACT_API_KEY>` header. (Verified working as of 2026-06.)
- **Submit (async):** `POST https://app.bettercontact.rocks/api/v2/async` with JSON body:
  `{ "enrich_email_address": true, "enrich_phone_number": true, "data": [ {"first_name","last_name","company","company_domain","linkedin_url"} ] }` — 1–100 contacts. Returns `{ "success": true, "id": "<request_id>" }`.
- **Poll:** `GET https://app.bettercontact.rocks/api/v2/async/{request_id}` with the `X-API-Key` header. `status` runs `"in progress"` → `"terminated"` (note the SPACE in "in progress" — match loosely / poll until it changes). When done you also get `credits_consumed`, `credits_left`, and a `data[]` array.
- **Per-record fields:** `contact_email_address`, `contact_email_address_status` (`deliverable` / `catch_all_safe` / `catch_all_not_safe` / `undeliverable`), plus the phone number.
- **Map status → confidence:** `deliverable` → `verified`, `catch_all_safe`/`catch_all_not_safe` → `likely`, `undeliverable` → exclude.
- **Why it's the default:** runs its own waterfall across 20+ providers and returns **email + validation + phone in one call**, and you only pay for valid data.

---

## Findymail (email/phone finder + verify) — `FINDYMAIL_API_KEY`
- **Docs:** https://www.findymail.com/api/ · Keys: https://app.findymail.com/user/api-tokens
- **Auth:** `Authorization: Bearer <FINDYMAIL_API_KEY>`, `Content-Type: application/json`.
- **Find email by name + domain:** `POST https://app.findymail.com/api/search/name` with JSON body `{ "name": "...", "domain": "..." }`.
- Also supports finding from LinkedIn, mobile lookup, and email verification — use as a fallback finder and/or validator.

---

## Prospeo (email + mobile finder) — `PROSPEO_API_KEY`
- **Docs:** https://prospeo.io/api-docs
- **Auth:** `X-KEY: <PROSPEO_API_KEY>`, `Content-Type: application/json`.
- **Mobile finder:** `POST https://api.prospeo.io/mobile-finder` with a LinkedIn URL — returns formatted phone numbers + country info.
- For email, use the current **Enrich Person** endpoint (the old standalone Email Finder is deprecated — confirm the current path in the docs).
- **Note:** returns `429` when rate-limited — back off and retry.

---

## Waterfall logic (how to combine them)
For each person missing an email after self-found attempts:
1. Try **BetterContact** (its own multi-source waterfall). If it returns a valid email, stop.
2. Else try **Findymail** (name + domain). If valid, stop.
3. Else try **Prospeo**. If still nothing, mark the person `no_email` and exclude from send.
4. **Validate** the winning email before it's used (BetterContact/Findymail validity flag, or a dedicated validator).

Stop at the first valid hit so you never pay two providers for the same contact. Log credits used per tool in the campaign's `reports/log.md`.

---

## Adding tools later
Apify, Instantly, Smartlead, and the enrichment trio are documented above. To add another tool — a **LinkedIn** sender like HeyReach, a **phone/dialer**, or a new enrichment source — add its key to `.env.example`, add a section here, and add a thin skill in `.claude/skills/`. Keep the same "read live docs first, dry-run, then batch" discipline.

> **Roadmap (next video):** a LinkedIn/Reddit **intent layer** (find people actively posting about a problem) + automated multi-channel delivery. Not wired yet.
