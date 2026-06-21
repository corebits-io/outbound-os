# Playbook 07 — Fetch Performance & Improve

**Goal:** Every few days, pull campaign performance from Instantly, diagnose what's working, and propose specific changes. This is what makes the system "ever-improving."

## Cadence
Run every 3–4 days while a campaign is live (the user can set this up as a scheduled task).

## Steps
1. **Pull analytics** from Instantly: `GET /api/v2/campaigns/analytics?ids=<campaign_id>` → opens, replies, bounces, unsubscribes per campaign (per-step and per-variant breakdowns too). See `reference/apis.md` (send the Cloudflare user-agent header).
2. **Write a snapshot** to `reports/<date>-performance.md`: the numbers, plus per-step and per-segment breakdown. Optionally mark each lead's disposition (`replied` / `bounced`) in `prospects/prospects.csv` to close the status loop (`pushed → replied/bounced`).
3. **Diagnose against benchmarks (the three axes):**
   - **Deliverability** — low open rate / high bounce → sending-health or list-quality problem (warmup, validation, spammy subject), *not* the copy. Fix this first; rewriting copy won't fix spam-foldering.
   - **Copy** — decent opens, low replies → the opener or offer angle isn't landing.
   - **Targeting** — replies but negative/irrelevant → wrong persona, wrong segment, or wrong promise.
4. **See what's responding.** Break replies down by segment / persona / angle / (for this kind of campaign) asset-type or vertical. Double down on the slice that's replying; rewrite or cut the slices that are silent. This is how the system learns the niche over time — not just "tweak the words."
5. **Propose changes, one variable at a time** so you can tell what moved the needle: a new Email 1 angle, a different persona, a tighter segment. Draft the variant.
6. **On approval,** update the sequence/campaign and note the change + date in `reports/log.md` so there's a history of what was tried.

## Schedule it (make it hands-off)
The loop is most valuable on autopilot. Once a campaign is live, run this playbook on a cadence so a Claude agent pulls the stats and reports back without you asking:
- Ask Claude to **schedule a recurring run** every 3–4 days — it can set up a scheduled agent / cron routine that re-runs this playbook against the live campaign.
- Each run writes a fresh `reports/<date>-performance.md` and surfaces the single change worth testing next.
- **You stay in the loop on _changes_** (approve before anything is rewritten or re-pushed); the **measuring + diagnosis happen automatically**. That's the "ever-improving campaign that tells you what isn't working" — running on its own.

## Guardrails
- Change one thing at a time; otherwise you can't learn.
- Distinguish a deliverability problem from a copy problem before rewriting copy — rewriting copy won't fix spam-foldering.
- Keep a simple before/after of the metric you're trying to move.

**Checkpoint:** Each run, give the user: current reply rate, the single biggest bottleneck, and the one change you recommend testing next.
