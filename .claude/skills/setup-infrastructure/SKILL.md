---
name: Setup Infrastructure
description: One-time sending setup — extra domains, inboxes, SPF/DKIM/DMARC, and warmup — so campaigns land in the inbox. Use once per sending setup, before the first real send. Claude preps; you buy and paste DNS.
allowed-tools: Read Write Edit WebFetch
---

# Setup infrastructure

Stand up deliverable sending infrastructure. **Claude preps; you click buy + paste DNS — no auto-spend.**

**Write:** `reference/infrastructure.md` (domains, inboxes, records, warmup start, and the "Cleared to send?" gate).

## Steps (full detail in `playbooks/00-infrastructure-setup.md`)
1. Plan domains + inboxes for your volume (never the main company domain).
2. Generate the exact SPF / DKIM / DMARC / MX records; you paste them; verify they're live.
3. Connect inboxes to the sender; turn on warmup (2–3 weeks).
4. Keep "Cleared to send?" = NO until warmup is healthy, then flip to YES.

**Rule:** never send from un-warmed inboxes. This gates `push-to-sequencer`.
