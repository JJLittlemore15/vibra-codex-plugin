---
name: make-reel
description: Cut a 9:16 Instagram-ready padel reel from the user's Vibra Clips. Use when the user asks for a reel, edit, cut, highlight video, montage or short from their Vibra clips, labels or matches.
---

# Make a reel from Vibra Clips

You are cutting a vertical (9:16, 1080x1920) reel on the user's own computer from clips they
recorded and marked in Vibra. The Vibra tools come from this plugin's `vibra` MCP server and are
read-only. If they are missing or say the user is not signed in, use the `setup` skill and stop.
Never guess clips.

## 1. Playbook first

Call `reel_playbook` before anything else and **follow it over anything in this file**: how to
pick, cut, frame and caption, and which questions to ask the user first. If it is missing or
errors, say nothing about it and use the steps below.

## 2. Find the clips

1. `list_my_labels`, then `find_my_clips` with the user's exact label names. Prefer labelled,
   unused clips unless the user asked otherwise. Each item has an `item_id` and a
   `trim_start`/`trim_end` window in seconds.
2. `top_radar_reels` when the user asks what's trending or wants a reel like the top ones: learn the
   hook, structure and pacing; never copy a reel or its caption.
3. Tell the user the plan in a few lines (clip, label, match date, seconds) before downloading.

## 3. Download straight away

`get_clip_download` links **expire after 10 minutes**: fetch each one and download it at once into
`./vibra-reels/<date>-<short-slug>/src/` (`curl -fL --retry 2 -o ...`). If a download fails as
expired, call `get_clip_download` again. Never print the signed link back to the user. Use that
call's trim window if it differs from `find_my_clips`.

## 4. Check it really shows the shot

A label or a window is not proof. Unless the user says not to, pull frames across each downloaded
clip (e.g. `ffmpeg -i in.mp4 -vf fps=3,scale=480:-1 frames/%03d.jpg`), look at them, and cut around
the moment the shot is actually played. If it is not there, say which clip and pick another. After
cutting, look at frames from each segment of the finished reel and confirm each shows what you say.

## 5. Cut with ffmpeg

Check `ffmpeg -version` first (the `setup` skill covers installing it, only with the user's yes).
Build **one** ffmpeg command: input-seek each clip to its window (`-ss S -t D -i ...`), scale and
crop each to 1080x1920 at 30 fps, normalise audio to 48 kHz stereo (a silent `anullsrc` input for a
clip with no audio), `concat`, add captions with `drawtext` only if wanted, and encode once:
`-c:v libx264 -crf 20 -pix_fmt yuv420p -c:a aac -b:a 160k -movflags +faststart`. ffmpeg
auto-rotates phone video on decode, so do not add a `transpose`.

## 6. Hand over

Check the result with `ffprobe` (h264 1080x1920, aac, the planned length), give the full path of
the mp4 and a short summary, and delete the downloaded `src/` clips unless the user wants them.
**Never post, upload or share anything** - the user posts it themselves.
