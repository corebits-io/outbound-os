# Outbound OS

> **👉 New here?** Download this folder — the green **Code** button → **Download ZIP** (or [grab the zip directly](https://github.com/corebits-io/outbound-os/archive/refs/heads/main.zip)) — unzip it, then open **`SETUP.md`**. It runs inside Claude Code; bring your own API keys.

A complete cold-outreach system that runs inside **Claude Code** (the version of Claude that lives in your terminal and can read, write, and run files on your computer).

Instead of bouncing between Clay, enrichment tools, and spreadsheets, the whole campaign lives in **one folder**. You fill in a few files describing the offer, and Claude Code does the rest: finds accounts, picks the right person, researches them, finds their contact info, writes the sequence, pushes it into your email tool, and checks back later to improve it.

Think of this folder as the **"brain"** from the post. You feed it the offer, it organizes everything, and then it operates.

---

## How it's organized (plain English)

- **`CLAUDE.md`** — The master instruction file. Claude Code reads this automatically every time it opens this folder. It's the "always-on rules" that tell Claude how to behave. You rarely edit this.
- **`master-build-prompt.md`** — The single message you paste into Claude Code the very first time, to wake the system up. Start here.
- **`campaigns/`** — One folder per client or offer. Copy `_TEMPLATE` to start a new one.
- **`playbooks/`** — Step-by-step instructions for each stage (sourcing, picking the person, research, enrichment, writing, sending, improving). Claude follows these so the output is consistent every time.
- **`reference/`** — Technical notes: how your APIs work, and the full pipeline at a glance.
- **`.env.example`** — A template for your secret keys (Instantly, BetterContact, etc.). You copy it to `.env` and paste your real keys in. *(An **API key** is just a password that lets your system log into another tool automatically — same idea as pasting a key into Clay or Instantly settings.)*

---

## How to use it (first time)

> **Fastest path: open `SETUP.md`** — it's the 5-minute front door. The short version is below.

1. **Install Claude Code** if you haven't — see `reference/getting-started.md`. ~15 minutes.
2. Open this `outbound-os` folder in Claude Code.
3. Copy `.env.example` to a new file named `.env` and paste in your real API keys.
4. Open `master-build-prompt.md`, copy everything, paste it into Claude Code, and hit enter.
5. Claude will ask you about your first campaign, then walk through the stages with you.

**Use plan mode for the big steps.** In Claude Code you can press `Shift+Tab` to enter *plan mode* — Claude tells you what it's about to do and waits for your "go" before touching anything. Use it for sourcing and sending. This is your safety net.

---

## The pipeline at a glance

First you **build the brain** — fill in the offer, ICP, personas, value prop, and past messaging. Then the **7 stages** run on top of it:

1. **Source accounts** — show it good-fit and bad-fit examples; it finds and qualifies more.
2. **Pick the right person** — it weighs role, who owns the problem, and signals (not just "the CEO").
3. **Research + find patterns** — it studies each account and builds the angle around real problems.
4. **Enrich only when needed** — finds data itself first, hits paid APIs only for the gaps.
5. **Write the sequence** — copy built from the research, not generic templates.
6. **Push to Instantly** — builds the campaign, attaches your **warmed** inboxes, sets the sending limits + settings, and loads the personalized leads. Never sends without your explicit go.
7. **Fetch + improve** — pulls performance every few days (can run on a schedule), shows what's landing by segment/angle, and changes one thing at a time. The loop that makes it better over time.

(There's also a one-time **stage 0 — stand up sending infrastructure**: domains, inboxes, and warmup, covered in `playbooks/00`.)

---

## A note on doing this safely and well

- **Warm up your sending domains and keep volume sane.** A great system sending from a cold domain still lands in spam. Instantly handles warmup — turn it on before you blast.
- **Respect the law.** Cold email is regulated (CAN-SPAM in the US, GDPR/PECR in Europe). Keep an opt-out, use real sender info, and don't email people where it isn't permitted. This system makes outreach faster — it's on you to keep it compliant.
- **Quality over volume.** The whole point of this build is better targeting and real personalization. Lean into that; don't turn it into a spam cannon.
