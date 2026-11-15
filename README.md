# Vibra Padel for Codex

Make padel reels from your Vibra Clips with Codex: find your best moments, get reel ideas from what's
trending on Vibra Radar, and cut 9:16 reels ready for Instagram. Skills `setup`, `make-reel` and
`brainstorm-reels`, plus the Vibra server.

Read-only: it sees your own clips and labels, and never posts, deletes or changes anything in Vibra or
on Instagram. You post the reels yourself.

## What you need

- A Mac or Windows PC with [Codex](https://developers.openai.com/codex) running on it
- A Vibra account with some clips
- [ffmpeg](https://ffmpeg.org) - on a Mac `brew install ffmpeg`, on Windows `winget install ffmpeg`

## Install

```bash
codex plugin marketplace add JJLittlemore15/vibra-codex-plugin
```

Then run `codex`, type `/plugins`, pick **Vibra Padel** and install it, sign in to Vibra when asked
(the same login as the app), and start a new session. Codex needs internet access allowed so it can
download your clips.

No plugin? On [vibrapadel.vercel.app/connect](https://vibrapadel.vercel.app/connect) copy the setup
prompt and paste it into Codex - it adds Vibra and signs you in.

Using Claude Code instead? See [vibra-claude-plugin](https://github.com/JJLittlemore15/vibra-claude-plugin).

## Privacy

[vibrapadel.shop/vibrapolicies](https://www.vibrapadel.shop/vibrapolicies)
