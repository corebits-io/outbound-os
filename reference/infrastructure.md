# Sending Infrastructure — status & gate

This file records your sending setup and whether you're **cleared to send**. Playbook 00 fills it in; Playbook 06 (Push) reads the "Cleared to send?" line before loading any campaign. Until it says **YES**, don't run real sends.

> This is a template. Replace the bracketed placeholders as you set things up. It's fine to leave it empty until you've run `playbooks/00-infrastructure-setup.md`.

---

## Cleared to send?
**Status:** `NO` — warmup not complete
**Cleared-to-send date (warmup start + ~2–3 weeks):** [DATE]

_Flip to `YES` only when every inbox below has finished warmup and shows healthy stats (see "Warmup health" at the bottom)._

---

## Sending domains
> Never the main company domain. Lookalike variants only.

| Domain | Registrar | Bought on | SPF | DKIM | DMARC | MX |
|---|---|---|---|---|---|---|
| [try-yourbrand.com] | [Namecheap] | [DATE] | ☐ | ☐ | ☐ | ☐ |
| [get-yourbrand.com] | [Namecheap] | [DATE] | ☐ | ☐ | ☐ | ☐ |

_Tick each record once it's pasted at the registrar **and** verified live._

## Inboxes
> Rule of thumb: ~3 inboxes per domain; ~20–30 emails/inbox/day **after** warmup.

| Inbox address | Domain | Mailbox host | Connected to sender? | Warmup on? | Warmup started |
|---|---|---|---|---|---|
| [jane@try-yourbrand.com] | [try-yourbrand.com] | [Google Workspace] | ☐ | ☐ | [DATE] |
| [john@try-yourbrand.com] | [try-yourbrand.com] | [Google Workspace] | ☐ | ☐ | [DATE] |

## Capacity
- **Inboxes total:** [N]
- **Safe daily volume after warmup:** [N inboxes × 25] ≈ [TOTAL] emails/day
- **Sender tool:** [Instantly]

## Warmup health (the "healthy" bar before flipping to YES)
- Warmup has run **at least 2–3 weeks**.
- Warmup open rate is steady and high (the sender's warmup dashboard shows it landing in inbox, not spam).
- Daily volume has ramped gradually, not spiked.
- No spam-folder placement in the warmup pool.

When all four are true, set **Cleared to send? → YES** and proceed to `playbooks/06-push-to-instantly.md`.
