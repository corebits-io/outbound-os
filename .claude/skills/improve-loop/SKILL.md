---
name: Improve Loop
description: Pull campaign performance every few days, diagnose deliverability vs copy vs targeting, see what's responding, and propose one change at a time. Use a few days after a campaign is live, or on a schedule.
allowed-tools: Read Write Edit Bash WebFetch
---

# Improve loop

Make the campaign better over time, on evidence.

**Read:** live analytics from the sequencer (see `reference/apis.md`).
**Write:** `campaigns/<campaign>/reports/<date>-performance.md`; log changes in `reports/log.md`.

## Steps (full detail in `playbooks/07-fetch-and-improve.md`)
1. Pull opens / replies / bounces / unsubscribes per campaign + step.
2. Diagnose the three axes: deliverability (opens/bounce) vs copy (replies) vs targeting (who replies).
3. See what's responding by segment / angle; double down on it, rewrite or cut the silent slices.
4. Propose ONE change; on approval, update + log it. Can run on a schedule (hands-off measuring; you approve changes).

**Rule:** change one variable at a time, or you can't learn what moved the needle.
