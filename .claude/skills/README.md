# Skills — the 12 building blocks of Outbound OS

Each folder here is a **real Claude Code skill**. Type `/` in Claude Code to run any of them, or just ask and Claude picks the right one. The detailed steps live in `playbooks/`; these skills are the entry points.

Run them in order for a full campaign (the master build prompt does this for you):

| # | Skill | What it does |
|---|---|---|
| 1 | `/source-accounts` | Find + qualify target companies (Apify if a token's set, else web) |
| 2 | `/qualify-icp` | Score against the ICP, drop bad fits |
| 3 | `/find-signals` | A real reason-to-reach-out per account |
| 4 | `/pick-person` | The right contact — not just the CEO |
| 5 | `/research-account` | Study each account + find patterns |
| 6 | `/find-verify-emails` | Find + verify emails (free first, paid only for gaps) |
| 7 | `/write-copy` | Short, personalized opener that probes, not pitches |
| 8 | `/build-sequence` | The full follow-up sequence + custom fields |
| 9 | `/preview-qa` | Human review of real emails before anything sends |
| 10 | `/push-to-sequencer` | Load a **DRAFT** into Instantly/Smartlead (never sends) |
| 11 | `/improve-loop` | Pull results, diagnose, change one thing |
| 12 | `/setup-infrastructure` | One-time domains / inboxes / warmup |

> New skills only register after a Claude Code restart. The hard rule lives in every send-related skill: **loading ≠ launching — nothing sends without your explicit "go."**
