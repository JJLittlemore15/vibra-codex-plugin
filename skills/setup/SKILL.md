---
name: setup
description: First-time setup for Vibra - sign in to Vibra, check the Vibra tools respond, and check ffmpeg is installed. Use when the user has just installed the Vibra plugin, asks how to connect or sign in to Vibra, or the Vibra tools are not working.
---

# Set up Vibra

Walk the user through these checks in order, briefly. Report each as done / needs action.

## 1. Sign in to Vibra

The plugin adds a remote MCP server called `vibra` (`https://vibrapadel.vercel.app/mcp`). Call its
`list_my_labels` tool.

- **Works** - the user is signed in. Say how many labels they have (names are fine to show).
- **Tool missing, or a sign-in / "needs authentication" error** - tell the user:
  1. Sign in to Vibra when Codex asks (it offers this when the plugin is installed). If it did not,
     type `/mcp` in Codex to see the Vibra server, or run `codex mcp login vibra` in a terminal.
  2. A Vibra page opens in the browser. Tap **Continue with Apple**, or enter the email used in the
     Vibra app and the 6-digit code Vibra emails. Then press **Allow**.
  3. Start a new Codex session and say "done".
  Then call `list_my_labels` again to confirm.
- **Signed in but no labels** - that is fine; labelling clips in the Vibra app (on the phone) makes
  them much easier to find here.

Access is read-only: the user's own clips and labels can be seen and downloaded to this computer;
nothing in Vibra can be posted, deleted or changed.

## 2. Playbook

Call `reel_playbook` once to confirm it responds. Do not show its contents.

## 3. Internet access and ffmpeg

Reels are cut on this computer with ffmpeg, from clips downloaded through short-lived links. If
Codex's sandbox blocks network access, tell the user it needs to be allowed for the downloads.

Run `ffmpeg -version` and `ffprobe -version`.

- **Both run** - done.
- **Not found** - suggest an install and **ask before running anything**: macOS `brew install ffmpeg`
  (Homebrew from https://brew.sh if missing), Windows `winget install ffmpeg`, Linux the distro package.
- **Found but fails to start** (e.g. "Library not loaded" on macOS) - suggest
  `brew update && brew upgrade ffmpeg`, again only with the user's yes.

## 4. Finish

Summarise what is ready and suggest a first ask, for example "Make me a 20-second reel of my best
points this week" or "Brainstorm reels from what's trending on Vibra Radar".
