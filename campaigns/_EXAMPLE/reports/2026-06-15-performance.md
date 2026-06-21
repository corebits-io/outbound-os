# Performance snapshot — 2026-06-15 (FICTIONAL SAMPLE)

Campaign: "Cohort — Scaling CS A" · Pulled from Instantly analytics · 7 days after load.

## Numbers
| Metric | Value | Read |
|---|---|---|
| Leads loaded | 12 | Segment A only |
| Delivered | 11 (92%) | 1 soft bounce (re-validate or drop) |
| Open rate | 58% | Healthy — deliverability looks fine |
| Reply rate | 17% (2 replies) | Strong for cold, but **small sample — directional only** |
| Positive replies | 1 | One "send me the teardown"; one "not this quarter" |
| Bounce rate | 8% (1) | Watch; one bounce on 12 is noise but re-check enrichment |
| Unsubscribes | 0 | — |

## Diagnosis (per Playbook 07)
- **Opens are healthy (58%)**, so this is *not* a deliverability problem — the domains/warmup are doing their job.
- **Replies are good but the sample is tiny (12).** Do not over-read one batch. The signal is "the angle is landing," not a precise rate.
- The 1 bounce slipped through validation — tighten the validation gate before the next push.

## One change to test next (change ONE thing)
- Rewrite **Email 1's subject** for the 5 non-openers' profile — test `{{observation_short}}` as a plain statement vs. a question. Keep body, persona, and segment identical so the subject is the only variable.

## Next actions
- Expand to **Segment B (Post-raise wave)** and **C (Product owns activation)** with their own angles.
- Re-validate the bounced lead; pull the next snapshot in 3–4 days.
