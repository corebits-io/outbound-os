---
name: Preview & QA
description: Show 5-10 prospects with their fully-personalized emails for human review BEFORE anything is loaded or sent — the quality gate most outreach skips. Use right before push-to-sequencer.
allowed-tools: Read Glob
---

# Preview & QA

The human checkpoint before any data leaves the folder.

**Read:** the active campaign's `prospects.csv`, `sequences/`, `research/`.
**Show the user (change nothing):** 5–10 prospects, each with — the picked person + `why_this_person`, the research hook, and the fully-merged email(s) exactly as they'll send.

## Check each
- Is the hook true + specific? Is the email short and a real probe (not a pitch)?
- Email confidence `verified`/`likely` (never `guess`)? Opt-out + sender present?
- Any merge field blank? Any account that shouldn't be contacted?

**Rule:** nothing proceeds to push until the user approves this preview. This is the differentiator — don't skip it.
