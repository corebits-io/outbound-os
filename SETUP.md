# SETUP — start here

The fastest path from "just downloaded the folder" to "it's running my campaign" — about **5 minutes if you already have Claude Code installed**; the first-time install in step 0 adds ~15. Do these steps in order; if you've used the terminal before, skip step 0.

---

## 0. (First time only) Install Claude Code — ~15 min
Follow [`reference/getting-started.md`](reference/getting-started.md). You install Node, then Claude Code, then open this folder. One-time.

## 1. Open this folder in Claude Code
In your terminal:
```
cd "path/to/outbound-os"
claude
```
Tip: open the same folder in VS Code in a second window so you can watch the files fill in as it works.

## 2. Paste in your keys
Make a copy of `.env.example` and name the copy `.env`, then paste your real API keys into it. Open `.env.example` — every line says what the key is for and where to get it.

**You do NOT need every key to start.** Minimum to do a full run:

| To do this... | You need |
|---|---|
| Build the brain, source, pick people, research, write copy | **Nothing — works out of the box** |
| Find emails/phones it couldn't find for free | at least one enrichment key (`BETTERCONTACT_API_KEY` is the best single one) |
| Actually load leads into a sending tool | `INSTANTLY_API_KEY` |

So you can start with **zero keys**, see the whole thing work, and add keys only when you hit the step that needs them. Your keys, your credits — this system never spends on your behalf without asking.

> `.env` is private. It is never shared, committed, or printed. Keep your keys out of screenshots and chats.

## 3. Wake it up
Turn on **plan mode** (press `Shift+Tab`), then open [`master-build-prompt.md`](master-build-prompt.md), copy the whole thing, paste it into Claude Code, and hit enter.

It will:
1. Tell you which keys it found (by name only) and what it can/can't do with them.
2. Ask you to name the campaign and create a folder for it under `campaigns/`.
3. Ask you about your offer and ICP, one question at a time, and fill in your campaign brain for you.
4. Lay out a plan for sourcing accounts and wait for your "go."

That's it. From there it walks you stage by stage. See a finished example of what it produces in [`campaigns/_EXAMPLE/`](campaigns/_EXAMPLE/).

---

### The two things only you can provide
1. **Your API keys** (step 2) — so it can use *your* tools and *your* credits.
2. **Your offer and who it's for** (step 3) — it asks; you answer.

Everything else — the workflow, the judgment, the writing — is already built in.

### If you get stuck
Copy the exact error text and paste it back to Claude in the session. Describing the precise error is the fastest way to get unstuck.
