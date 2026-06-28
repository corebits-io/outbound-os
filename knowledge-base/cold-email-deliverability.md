# Cold email deliverability — the basics that keep you out of spam

A perfect system sending from a cold domain still lands in spam. Get this right *before* you send.

## Domains & inboxes
- **Never send cold from your main company domain.** Buy separate lookalike domains (e.g., `try-yourbrand.com`).
- ~**3 inboxes per domain**; ~**20–30 emails / inbox / day** after warmup. Need more volume → more inboxes, not more per inbox.

## Authentication (the 3 records)
- **SPF** — says which servers may send for your domain.
- **DKIM** — a signature proving the mail wasn't tampered with.
- **DMARC** — tells receivers what to do if SPF/DKIM fail.
Set all three per sending domain (Playbook 00 generates the exact records). This is the single biggest inbox-vs-spam factor.

## Warmup
- Turn on warmup on every inbox and let it run **2–3 weeks** before real sends.
- Keep "Cleared to send?" = NO in `reference/infrastructure.md` until warmup is healthy.

## Tracking (a real trade-off)
- **Open tracking** (pixel) and **link tracking** can *hurt* deliverability. If you can live without open data, turn them off. Reply rate is the metric that matters most anyway.

## Stay out of the spam folder
- Keep emails short and human; avoid spammy words/ALL CAPS/lots of links.
- Validate every email first; never send to `guess` or `catch-all-not-safe` addresses.
- Ramp volume gradually; pause if bounce rate climbs.

## Compliance (not optional)
- **CAN-SPAM (US):** a real opt-out + a physical mailing address + honest sender info, every email.
- **GDPR / PECR (EU/UK):** stricter — have a lawful basis; don't email where it isn't permitted.
- The system makes outreach faster; keeping it legal is on you.
