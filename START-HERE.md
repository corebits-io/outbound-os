# START HERE — the full runbook

This is the ordered, do-this-then-that guide. Three phases:
1. **Run it yourself** (prove it works, get sends out).
2. **Share it** with the LinkedIn commenters.
3. **Build it properly + replicate for clients + make it YouTube-ready.**

---

## First: does the kit match the post? (quick sanity check)

| Your post said | Where it lives in the kit |
|---|---|
| 1. Build the brain (offer, ICP, personas, value prop, past messaging → one folder) | `campaigns/_TEMPLATE/01–04` + `CLAUDE.md` |
| 2. Source accounts (good/bad examples → find + qualify more) | `playbooks/01-source-accounts.md` |
| 3. Pick the right person (not just the CEO) | `playbooks/02-pick-the-person.md` |
| 4. Write from research (patterns, real problems) | `playbooks/03-research-and-patterns.md` + `05-write-sequences.md` |
| 5. Enrich only when needed (free first, paid for gaps) | `playbooks/04-enrich-and-validate.md` |
| (+ what the post implied) Push to sender + improve over time | `playbooks/06-push-to-instantly.md` + `07-fetch-and-improve.md` |

So the kit covers all five steps in your post, plus the send + improve loop. Good to go.

*(It's now also built as **12 invokable skills** in `.claude/skills/` — matching the "12+ skills" post — plus a `knowledge-base/` of context docs and the 4-tool stack: Claude Code · Apify · BetterContact · Instantly/Smartlead.)*

---

# PHASE 1 — Run it yourself

Do this first. You want proof it works *before* you hand it to anyone or film it.

**Step 1 — Install Claude Code.** Follow `reference/getting-started.md` (~15 min). One-time.

**Step 2 — Open the folder in Claude Code.** In your terminal:
```
cd "path/to/outbound-os"
claude
```
*`cd` moves the terminal into this folder so Claude works on these files; `claude` starts it.* Tip: open the same folder in VS Code in a second window so you can watch files change.

**Step 3 — Add your keys.** Copy `.env.example` to a new file named `.env`, paste your real Instantly + enrichment keys. *(The `.env` file is private — it never gets shared.)*

**Step 4 — Wake the system up.** Turn on plan mode (`Shift+Tab`), then paste the contents of `master-build-prompt.md` and hit enter. Claude will confirm the pipeline and check your keys.

**Step 5 — Build the brain for ONE real offer.** Claude will ask you questions and fill in `01–04` for your first campaign. Use a real offer you actually sell — that's how you'll know the output is good.

**Step 6 — Run stages 1–5, checkpointing each.** Source → pick person → research → enrich → write. Keep batches small (e.g., 25 accounts) and eyeball the quality before continuing. Correct Claude when a pick or angle is off — it learns within the run.

**Step 6.5 — Set up sending infrastructure (if you haven't).** Run `playbooks/00-infrastructure-setup.md`. Claude preps everything — recommends domains, generates your exact SPF/DKIM/DMARC records, gives the click-path, and sets a warmup plan — but **you** click buy and paste DNS. Warmup needs 2–3 weeks before real sends, so start this early (you can run it in parallel with building the brain).

**Step 7 — Push a SMALL test to Instantly.** Load 2–3 leads first, preview how they render, approve, then load the rest. Confirm your domains are warmed up before any sending.

**Step 8 — Let it run, then improve.** After a few days, run `playbooks/07` to pull stats and get a recommended change. This is the loop that makes it better over time.

> When you've done one full pass and like the output — that's your proof. Now you can confidently give it away and film it.

---

# PHASE 2 — Share it with the LinkedIn commenters

You're giving them the *system* (the folder), minus your private keys. They add their own.

**What they receive:** the whole `outbound-os` folder with `.env.example` (template, no real keys) — never your `.env`. `SETUP.md` is their 5-minute front door; the README and the filled `campaigns/_EXAMPLE/` show them what good looks like.

**Three ways to share — pick based on who's receiving:**

1. **A ZIP file (simplest, works for everyone).** Ask Claude Code to build a clean share zip — it copies the folder, drops your `.env` and any real campaign data, and keeps `_TEMPLATE` + the `_EXAMPLE` campaign. DM or email the zip. Best for non-technical commenters.
2. **A GitHub repo (best for credibility + your YouTube video).** A free, public web page holding the folder; people click "Download ZIP" or clone it. Looks professional on camera and lets you update it over time. I can walk you through creating this when you're ready (~15 min, one-time).
3. **A Google Drive / Notion link.** Upload the folder, share a view link. Easy to browse, easy to send in bulk.

**Recommendation:** ZIP now for the comment replies; spin up the GitHub repo before you film the YouTube video.

**A DM template to send with it:**
> Hey [name] — here's the Outbound OS build I mentioned. Open `SETUP.md` first, it gets you running in about 5 minutes. You can start with zero API keys and add your own Instantly + enrichment keys when you hit the steps that need them (`.env.example` shows where they go). There's a fully worked example campaign inside so you can see the output. Built it to run entirely inside Claude Code — would love to hear what you think once you try it.

**A quick public reply to the comment (then DM the kit):**
> Sent you a DM with the full build 🙌 Open `SETUP.md` first — you can have it running in ~5 min, and there's a complete example campaign inside.

**Before you share, the safety checklist:**
- Confirm there's **no `.env`** in what you send — only `.env.example`. (The clean-zip step excludes it automatically; still eyeball the contents once before sending.)
- Remove any real campaign folders with client data — share only `_TEMPLATE`.
- Tell recipients plainly: use *their own* API keys, and keep sending compliant (opt-out, real sender info, warmed domains).

---

# PHASE 3 — Build it properly + replicate + show it off

**For yourselves (the "real" version).** When you've run a few campaigns and know what matters, we write a deeper *technical spec* and have Claude Code build the standalone coded app: scripts that run the pipeline deterministically, a small database for leads, and scheduled jobs so stage 7 runs itself. I'll write that spec with you when you're ready — running Phase 1 first is what makes the spec good.

**Replicate for clients.** Each new client = copy `campaigns/_TEMPLATE` to a new campaign folder and fill in their brain. The playbooks and wiring stay the same. That's your repeatable service delivery.

**YouTube-ready.** The clean structure (one folder, clear files, plan-mode walkthrough) films well. The strongest demo is a screen recording of Phase 1 happening live — empty brain to loaded campaign — with the GitHub repo linked in the description as the giveaway.

---

## If you get stuck
Copy the exact error text and paste it to Claude in the session — describing the precise error is the fastest path to unstuck. And keep using this claude.ai project to plan and ask "how do I…" questions; it has the training videos to draw on.
