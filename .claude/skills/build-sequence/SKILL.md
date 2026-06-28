---
name: Build Sequence
description: Turn the approved opener into a full short sequence (follow-ups + delays) and define the personalization custom fields and the leads-upload file. Use after the opener is approved, before pushing to the sequencer.
allowed-tools: Read Write Edit
---

# Build sequence

**Read:** the approved opener, `research/_patterns.md`, `03-value-prop-and-messaging.md`.
**Write:** `campaigns/<campaign>/sequences/sequence-<segment>.md` (3–4 emails + delays; sensible default Day 0 / 3 / 6 / 10), `sequences/custom-fields.md`, and `sequences/leads-upload.csv`; set covered prospects to status `written`.

## Steps (full detail in `playbooks/05-write-sequences.md`)
1. Per segment, write 3–4 emails — each a new angle or proof, never "just bumping this up."
2. List every `{{variable}}` in `custom-fields.md` so the push step can map columns.
3. Compliance: real opt-out + honest sender info; only provable claims.

**Rule:** one segment = one sequence. Keep every email short.
