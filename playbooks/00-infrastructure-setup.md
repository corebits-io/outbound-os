# Playbook 00 — Infrastructure Setup (guided, no auto-spend)

**Goal:** Get sending infrastructure ready — extra sending domains, inboxes, authentication, and warmup — so your campaigns land in the inbox. This is the "Stand up the infrastructure" step.

**Important principle: Claude preps, you click buy.** Buying domains and editing DNS touches real money and your deliverability. One wrong record or a rushed purchase can burn a domain. So Claude does all the thinking and generates the exact configs — **but never spends money or changes DNS on its own.** You execute the purchase and paste the records. (If you later want true auto-provisioning, that's a Phase 2 build with explicit approval gates.)

## Steps

1. **Plan domains & inboxes.** Based on your target sending volume, Claude recommends how many sending domains and inboxes you need. Rules of thumb: never send cold from your main company domain; ~3 inboxes per domain; ~20–30 emails/inbox/day *after* warmup. Claude proposes lookalike domain names (variants of your brand). You buy them at a registrar (Namecheap, Cloudflare, or Porkbun — roughly $10/domain/year).

2. **Authentication records.** For each domain, Claude generates the exact **SPF, DKIM, DMARC, and MX records** to paste into your DNS settings. *(These are the records that tell receiving servers your mail is legitimate — the single biggest difference between landing in inbox vs. spam.)* Claude explains what each one does. You paste them at the registrar; Claude can then help you verify they're live.

3. **Connect inboxes to your sender.** Create the mailboxes (Google Workspace, Outlook, or your sequencer's own inboxes), then connect them in Instantly. Claude gives you the exact click-path.

4. **Turn on warmup.** Enable warmup on every inbox in Instantly and let it run **2–3 weeks** before any real sending. Claude notes the schedule and a sensible volume ramp.

5. **Record it + set the gate.** Fill in `reference/infrastructure.md` as you go (domains, inboxes, which records are live, warmup start dates). Keep **"Cleared to send?"** at `NO` until warmup is healthy, then flip it to `YES`. Playbook 06's pre-flight reads that exact line before any real send.

## Guardrails
- Claude **never** purchases anything or edits DNS for you. It prepares; you do the money + DNS steps.
- Never send cold from your primary domain.
- Treat warmup as non-negotiable — great targeting + sharp copy still lands in spam from a cold domain.

## Output
`reference/infrastructure.md` recording your domains, inboxes, the records you set, and warmup start dates — so the system knows when you're cleared to send.
