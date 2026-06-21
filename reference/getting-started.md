# Getting Started with Claude Code (for non-developers)

If you've never used the terminal, this is the 15-minute version. Do it once.

## What you're installing
- **Terminal** — the black window where you type commands instead of clicking. On Mac it's the app called "Terminal"; on Windows use "PowerShell."
- **Node.js** — the engine Claude Code runs on. (Like how Clay needs a browser, Claude Code needs Node.)
- **Claude Code** — Claude that lives in your terminal and can read/write files in a folder and run things.

## Steps

1. **Install Node.js** (version 18+). Easiest path: download the "LTS" installer from https://nodejs.org and run it. To check it worked, open Terminal and type:
   ```
   node --version
   ```
   **What this does:** asks your computer which version of Node it has. You should see a number like `v20.x`. If you see an error, the install didn't finish — re-run the installer.

2. **Install Claude Code.** In Terminal, type:
   ```
   npm install -g @anthropic-ai/claude-code
   ```
   **What this does:** `npm` is the installer that came with Node. `-g` means install it "globally" so you can use it from any folder. This downloads Claude Code onto your computer.

3. **Open this campaign system in Claude Code.** Point the terminal at this folder, then start Claude:
   ```
   cd "path/to/outbound-os"
   claude
   ```
   **What this does:** `cd` ("change directory") moves the terminal into the `outbound-os` folder so Claude works on these files. `claude` starts it. The first time, it'll ask you to log in with your Claude account.

4. **Plan mode is your friend.** Once inside, press `Shift+Tab` to toggle *plan mode* — Claude describes what it'll do and waits for your OK before changing anything. Use it for sourcing and sending.

## You're ready
Go back to the main `README.md`, set up your `.env` keys, then paste in `master-build-prompt.md`.

> Stuck on an error? Copy the red text and paste it to Claude — describing the exact error is the fastest way to get unstuck.
