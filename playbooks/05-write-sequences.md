# Playbook 05 — Write the Sequence

**Goal:** Produce email sequences built on the research and patterns — not generic templates. Save to `sequences/`.

## Inputs
- `03-value-prop-and-messaging.md`, `research/_patterns.md`, per-account research notes.

## Approach
1. **Write per segment, personalize per account.** Use the segments/patterns from Playbook 03 to set the angle. Then weave in the one true, specific observation from each account's research note. Personalization = relevance, not just `{{first_name}}`.
2. **Structure:** a short sequence of 3–4 emails:
   - Email 1: a sharp, relevant opener tied to their situation + soft value + light ask.
   - Email 2–3: new angle or proof each time (don't just "bumping this up").
   - Final: a clear, easy out / breakup.
   Follow the tone, length, and CTA rules in `03-value-prop-and-messaging.md`. Respect the banned-words list.
3. **Personalization variables.** Decide which pieces are per-lead custom fields (e.g., `{{observation}}`, `{{company}}`) so they map cleanly into Instantly columns later.
4. **Compliance basics.** Include a real opt-out and honest sender info. Keep claims to what's provable in the value-prop file.

## Output
- `sequences/sequence-<segment>.md` — full copy for each email with timing/delays. Sensible default cadence if you have no preference: Day 0, Day 3, Day 6, Day 10.
- A `sequences/custom-fields.md` note listing every `{{variable}}` used, so the push step knows what columns the CSV needs.
- Set `status` → `written` in `prospects/prospects.csv` for every prospect now covered by a finished sequence.

**Done when:** each segment has a complete sequence, `custom-fields.md` lists every variable used, and the prospects those sequences cover are at `status = written`.

## Quality bar (self-check before finishing)
- Could this email have been sent to 1,000 companies unchanged? If yes, it's too generic — add the research hook.
- Is every claim true and provable? Is the ask easy to say yes to?
- Subject lines: short, curiosity or relevance, no spammy words.

**Checkpoint:** Show the user the full sequence for one segment + 2 personalized examples before generating across the list. Then move to Playbook 06.
